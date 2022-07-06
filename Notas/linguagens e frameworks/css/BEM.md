**BLOCO** | *entidade autônoma que é significativa por si só. É um componente, pode inclusive haver componente dentro componente*
- Ex: header, footer, checkbox
  
```css
.menu {  }
```

**ELEMENTO** | *Parte de um componente (filho).*
- Ex: item de menu, item de lista, label do checkbox
  
```css
.menu__item, .menu__link {  }
```

**MODIFICADOR** | *uma variante de um componente ou elemento*
- Ex: disabled, checked, full-width, dark, light, active, enabled

```css
.menu--dark, .menu--checked, .menu--active {  }
```

- Ex: modificador de item

```css
.menu__item--dark, .menu__link--checked, .menu__item--active {  }
```

---

### EXEMPLOS

```html
<article class="card">
    <div class="card__header">
        <h1 class="card__title"></h1>
    </div>

    <div class="card__content">
        <img src="" alt="" class="card__image">

        <p class="card__text">
            Lorem ipsum
        </p>

        <p class="card__text">
            Lorem ipsum dolor sit
            <a href="" class="card__link">meet</a>

            <button class="button button--large">Click me</button>
        </p>
    </div>
</article>
```

```css
.c-card {}

.c-card__header {}

.c-card__title {}

.c-card__content {}

.c-card__image {}

.c-card__text {}

.c-card__link {}

.c-button {}
.c-card .button {} /* se ativar em todos os buttons do card */
.c-card__text .button {} /* se ativar apenas em card__text */
.c-card__text .button--large {} /* modificador */

.c-menu--small .c-menu__link {} /* Item dentro de um modificador */
```

---

SMACSS

- Base: coisas não semânicas, como variáveis, normalize
- Layout: coisas reutilizáveis sem semântica como lowerCase, active, mixins
- Module: card, panel, modal
- State: active, dark, light, large, medium
- Theme: temas do sistema