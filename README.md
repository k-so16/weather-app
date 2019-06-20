# weather-app
- electron-vue の教育用リポジトリ
- お天気アプリっぽいものを作る

## セットアップ
1. リポジトリをクローン

    ```bash
    git clone https://github.com/k-so16/weather-app.git
    ```

1. Node.js のパッケージをインストール

    ```bash
    npm install
    ```


## 実行
以下のコマンドでプログラムを実行

  ```bash
  npm run electron:serve
  ```

## ビルド
以下のコマンドでネイティブアプリケーションにコンパイル

  ```bash
  npm run electron:build
  ```


## 手動による環境構築
1. Vue-CLI 3 をインストール

    ```bash
    npm install @vue/cli -g
    ```
1. Vue-CLI でプロジェクトを作成
    - Vuex, Vue Router などのパッケージのインストールはお好みで

    ```bash
    vue create weather-app
    ```

1. electron-builder をインストール

    ```bash
    cd weather-app
    vue add electron-builder
    ```
