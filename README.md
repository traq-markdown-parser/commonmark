# CommonMark and reusable extensions

CommonMark 0.31.2 と汎用 Markdown 拡張の文法・ノード契約・テキスト描画を所有します。

| crate | 責務 |
| --- | --- |
| `markdown-commonmark-contracts` | CommonMark の型付きノード |
| `markdown-commonmark` | CommonMark の構文解析 |
| `markdown-commonmark-text` | CommonMark AST のテキスト描画 |
| `markdown-generic-contracts` | 数式、表、取り消し線、mark のノード契約 |
| `markdown-generic-syntax` | 汎用拡張の構文解析 |
| `markdown-generic-text` | 汎用拡張のテキスト描画 |

各機能は独立した crate として利用できます。契約と構文実装は同じリポジトリで管理し、ノードを読むだけの処理が構文解析へ依存する必要はありません。

## 開発

```sh
cargo test --locked --workspace --all-features
cargo fmt --all --check
cargo clippy --locked --workspace --all-targets --all-features -- -D warnings
```

Rust の版は `rust-toolchain.toml`、外部依存の版は manifest と `Cargo.lock` で固定しています。core は Git の確定 revision から取得されるため、他の checkout は不要です。CommonMark の652仕様例を同梱して検証します。出典・ライセンスは [fixtures](tests/fixtures/README.md) を参照してください。

## 境界

依存先は [core](https://github.com/traq-markdown-parser/core) です。traP / traQ の文法・preset・アプリケーション方針は知りません。

traQ 用の構成は [trap](https://github.com/traq-markdown-parser/trap)、Wasm と TypeScript / Go bindings は [sdk](https://github.com/traq-markdown-parser/sdk)、HTML と CSS は [traq-markdown-it](https://github.com/traPtitech/traq-markdown-it) にあります。
