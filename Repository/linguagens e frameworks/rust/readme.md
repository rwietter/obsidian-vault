# Rust

- Rust é extremamente rápido e gerencia memória eficientemente: sem runtime ou garbage collector, podendo potencializar a performance de serviços críticos, rodar em sistemas embarcados, e facilmente integrar-se a outras linguagens.
- O rico sistema de tipos de Rust e seu modelo de ownership garantem segurança de memória e segurança de concorrência — e permite que você elimine muitas categorias de erros durante a compilação.
- Rust possui uma ótima documentação, um compilador amigável com mensagens de erros úteis, e ferramental de primeira qualidade — uma ferramenta integrada de compilação e gerenciamento de pacotes, suporte inteligente para múltiplos editores com autocompleção e inspeções de tipos, um formatador automático, e muito mais.

---

### Instalando Rust

```bash
# Add export PATH="$HOME/.cargo/bin:$PATH" to .zhrc

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

---

### Guides

- [Start](https://gist.github.com/vit0rr/136226b267603c37749c324103ad62f8)
- [The Rust Programming Language](https://doc.rust-lang.org/stable/book/)
- [A Linguagem de Programação Rust](https://livro.rustbr.org/)
- [Rustlings](https://github.com/rust-lang/rustlings)
- [Rust4Noobs](https://github.com/pgjbz/rust4noobs)
- [Crust of Rust](https://www.youtube.com/watch?v=rAl-9HwD858&list=PLqbS7AVVErFiWDOAVrPt7aYmnuuOLYvOa)
- [Meet Rocket](https://rocket.rs/)

---

### Tooling

- [Cargo](https://doc.rust-lang.org/cargo/index.html): é o gestor de sistemas e pacotes da linguagem Rust
  - compile seu projeto com `cargo build`
  - execute seu projeto com `cargo run`
  - teste seu projeto com `cargo test`
  - gere a documentação do seu projeto com `cargo doc`
  - publique sua biblioteca em crates.io com `cargo publish`
- RLS: Rust Language Server
- Racer: code completion
- Rustfmt: format rust code
- Rustup: Rust toolchain installer

---

### Executar e compilar

- Para compilar e executar basta executar `rustc index.rs`
- Para compilar a aplicação em uma rede, basta executar `cargo build --release`
- Para executar a aplicação com watch mode, basta instalar o cargo-watch com `cargo install cargo-watch` e executar `cargo watch -x run`
- `cargo check` verificará rapidamente seu código para garantir que ele seja compilado corretamente.

```rust
/* init point to start with rust */
fn main() {
  let x = 5;
  let y = 10;
  let sum = x + y;
  
  println!("Sum of {} + {} = {}", x, y, sum);
}
```

---

Observações:

- Em Rust, pacotes de código são referidos como crates