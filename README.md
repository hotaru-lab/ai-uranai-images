## 画像フォルダの作成・画像追加手順

カード画像は `ai-uranai-images` リポジトリでデッキごとにフォルダを分けて管理する。

### 1. デッキ用フォルダを作成

GitHubで `ai-uranai-images` を開く。

**Add file → Create new file**

を選択する。

ファイル名に、

`Deck_ID/.gitkeep`

と入力してファイルを作成する。

例：

`wildflower_lovers_lenormand/.gitkeep`

これで、

```text
ai-uranai-images/
└─ wildflower_lovers_lenormand/

という画像フォルダが作成される。

2. 画像をアップロード

作成したデッキフォルダを開き、

Add file → Upload files

を選択する。

リネーム済みのカード画像をまとめてアップロードする。

3. ファイル名のルール

カード画像は、

カードID_英語名.png

の形式に統一する。

例：

WL001_Rider.png
WL002_Clover.png
WL003_Ship.png

カバー画像は、

WL_cover.png

とする。

4. フォルダ構成

最終的には以下のようにする。

ai-uranai-images/
└─ Deck_ID/
   ├─ DeckID_cover.png
   ├─ DeckID001_カード名.png
   ├─ DeckID002_カード名.png
   └─ …

例：

ai-uranai-images/
└─ wildflower_lovers_lenormand/
   ├─ WL_cover.png
   ├─ WL001_Rider.png
   ├─ WL002_Clover.png
   ├─ WL003_Ship.png
   └─ …
   └─ WL036_Cross.png
5. 画像URL

画像はGitHubのRaw URLでアプリから読み込む。

基本形：

https://raw.githubusercontent.com/hotaru-lab/ai-uranai-images/main/Deck_ID/ファイル名

例：

https://raw.githubusercontent.com/hotaru-lab/ai-uranai-images/main/wildflower_lovers_lenormand/WL001_Rider.png

### 注意
フォルダ名は Deck_Master の Deck_ID と完全に一致させる。
カード画像のファイル名は Card_DB_Master のカードID・英語名と一致させる。
英語名のスペースは _ にする。
ファイル名の大文字・小文字も統一する。
カード番号はデッキ内のカードIDに合わせる。
カバー画像は DeckID_cover.png とする。
