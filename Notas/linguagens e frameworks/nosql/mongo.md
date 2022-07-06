## MongoDB

MongoDB é um banco de documentos baseado em collections que armazenam BJSON. Além dos tipos genéricos e objetos, ele permite minKey, maxKey, Timestamp, BinData, ObjectId, Data, Regular Expressions.

É possível participar collections em partes menores via Sharding, ou seja, digamos que tenho uma collection de 3 TB, posso dividir ela por data em três collections em diferentes máquinas que dão 1TB cada.

ObjectId é um campo cujo MongoDB utiliza para identificar o registro e caso ele não passo passado explicitamente, o MongoDB vai fazer isso de forma implícita automaticamente.

### Find

```ts
dB.collection.count();
dB.collection.find();
dB.collection.findOne();

// Where
dB.collection.find({ _id: 73, name: "John Doe" }).pretty();
await UserModel.findOne(
  { email: "jhondoe@gmail.com" },
  { _id: 0, createdAt: 0, updatedAt: 0 }
);

// Find by name and only includes name and age
dB.collection.find({ name: "John Doe" }, { name: true, age: true }).pretty();
```

### Insert

Para inserir dados utilizamos o método `insert` ou `insertMany`

```js
await UserModel.insertMany({
  firstName: "John",
  lastName: "Doe",
  email: "johndoe@mail.com",
});
```

No mongoDB podemos armazenar estruturas com mais ou menos campos em uma mesma collection, por exemplo:

```js
await UserModel.insertMany({ firstName: "John", lastName: "Doe" });
await UserModel.insertMany({
  firstName: "Johnny",
  lastName: "Brabo",
  email: "jhonnybrabo@mail.com",
});
await UserModel.insertMany({ firstName: "Jhow" });
```

### UPDATE

Por padrão o MongoDB atualiza apenas o primeiro registro encontrado, para alterar vários é necessário especifar como argumento `multi: true` para atualizar vários registros.

Além disso, no MongoDB é possível também alterar a estrutura da collection e remover colunas:

```js
await UserModel.updateOne(
  { email: "johndoe@gmail.com" },
  { firstName: "Jhonny" }
);

// remove as outras colunas que não foram citadas
await UserModel.updateOne(
  { email: "johndoe@gmail.com" },
  { firstName: "Jhonny", lastName: "Doe" }
);

// Não remove as outras colunas
await UserModel.updateOne(
  { email: "johndoe@gmail.com" },
  { $set: { firstName: "Jhonny", lastName: "Doe" } }
);
```

### Upsert

Esse método vai atualizar um dado caso ele exista ou inserir caso ele não exista.

```js
// Atualiza esse dado adicionando o CPF caso ele não exista
await UserModel.updateOne({ email: 'mauriciobw17@gmail.com' }, { $set: {  CPF: '04634226419' } })
```

### Delete

