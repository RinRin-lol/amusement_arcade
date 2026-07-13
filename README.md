# みんなのゲーム屋 - Googleフォーム/スプレッドシート連携版

## ファイル構成

```text
index.html
styles.css
app.js
```

3ファイルを同じフォルダに置き、`index.html` を開くと動きます。

## 想定する運用

```text
子供たちがGoogleフォームで投稿
  ↓
回答がGoogleスプレッドシートに溜まる
  ↓
運営が「公開可否」列を 公開 にする
  ↓
サイトが公開CSVを読み込む
  ↓
ゲーム機として表示
```

## Googleフォーム項目例

- ゲーム名
- ニックネーム
- 学年区分
- ゲームURL
- スクリーンショット画像
- コメント
- 公開可否

## app.jsで必ず設定するところ

```js
const CONFIG = {
  SHEET_CSV_URL: 'ここに公開CSV URLを入れる',
  FORM_URL: 'ここにGoogleフォームURLを入れる',
};
```

## 公開可否について

`CONFIG.REQUIRE_APPROVAL` が `true` の場合、公開可否列が以下の値の行だけ表示されます。

```text
公開 / OK / TRUE / yes / 1 / publish / published
```

## Google Drive画像について

GoogleフォームのファイルアップロードでDriveに保存された画像URLは、サイト側で表示用サムネイルURLに変換します。
ただし、画像ファイルの共有設定が閲覧可能になっていないと表示されません。
