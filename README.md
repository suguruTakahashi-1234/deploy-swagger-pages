# deploy-swagger-pages

### 概要

以下の 2 点を検証したリポジトリになります。

- メインの検証
  - GitHub Actions の [swagger-ui-action](https://github.com/Legion2/swagger-ui-action) を用いて `openapi.yaml` の更新をトリガーに Swagger での API 仕様書を GitHub Pages にデプロイする検証
- サブの検証
  - GitHub Actions を用いて `openapi.yaml` の更新をトリガーに、iOS リポジトリに対して [swift-openapi-generator](https://github.com/apple/swift-openapi-generator) で生成されたコードの変更の PR を作成する Workflow の検証
    - 今回はサンプルとして、[swift-openapi-gen-sample](https://github.com/suguruTakahashi-1234/swift-openapi-gen-sample) というリポジトリに対して [repository-dispatch](https://github.com/peter-evans/repository-dispatch) を用いて、GitHub Actions の workflow を kick する

### Swagger UI

- https://sugurutakahashi-1234.github.io/deploy-swagger-pages/

### Step

![](./assets/step1.png)

### Lisks

- Swagger Editor
  - https://editor.swagger.io/
- Swaggerで作成したAPI仕様書をGitHub Pagesにデプロイしよう！
  - https://qiita.com/shun198/items/520806a86a14a4bd64a8
- GitHub Pages サイトの公開元を設定する
  - https://docs.github.com/ja/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- GitHub Actions
  - https://github.com/actions/upload-artifact
  - https://github.com/Legion2/swagger-ui-action
  - https://github.com/actions/deploy-pages


### OpenAPI to PDF Converter

#### Prerequisites

- Node.js and npm installed.

#### Setup

1. Install the required dependencies.

   ```bash
   npm install
   ```

#### Generate PDF

1. **Generate Asciidoc**: Use `openapi-generator-cli` to generate Asciidoc files from the OpenAPI YAML file.

   ```bash
   npm run generate-asciidoc
   ```

2. **Generate PDF**: Use `asciidoctor-web-pdf` to convert the generated Asciidoc files to PDF with the custom theme.

   ```bash
   npm run generate-pdf
   ```

3. **Convert Asciidoc to PDF**: A combined script that generates Asciidoc and then converts it to PDF.

   ```bash
   npm run convert-asciidoc
   ```

#### Custom Theme

The custom theme file `theme.yml` includes settings to improve the readability of the generated PDF. This theme uses the NotoSansJP font for better Japanese text rendering.

