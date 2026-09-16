## 画像フォルダの作成・画像追加・リネーム手順

カード画像は `ai-uranai-images` リポジトリで、デッキごとにフォルダを分けて管理する。

### 1. デッキ用フォルダを作成

GitHubで `ai-uranai-images` リポジトリを開く。

**Add file → Create new file** を選択する。

ファイル名に `Deck_ID/.gitkeep` と入力してファイルを作成する。

例：

`wildflower_lovers_lenormand/.gitkeep`

これで `wildflower_lovers_lenormand` という画像フォルダが作成される。

### 2. 画像を準備

取得したカード画像をデッキごとの作業フォルダに保存する。

この時点では、画像ファイル名が数字だけでもよい。

例：

`1.jpg`
`2.jpg`
`3.jpg`

カード番号とCard_DB_Masterのカード情報の対応を確認してからリネームする。

### 3. ファイル名をリネーム

カード画像は以下の形式に統一する。

`Card_ID_English_Name.拡張子`

例：

`WL001_Rider.png`
`WL002_Clover.png`
`WL003_Ship.png`

English_Name内のスペースは `_` に置き換える。

例：

`Between Worlds` → `Between_Worlds`

`Not for You` → `Not_for_You`

元画像の拡張子は維持する。

`.jpg` → `.jpg`
`.png` → `.png`
`.webp` → `.webp`

英語名の大文字・小文字は、Card_DB_Masterの `English_Name` を基準とする。

### 4. PowerShellで一括リネーム

カード番号とEnglish_Nameの対応が確認できている場合は、PowerShellを使用して一括リネームできる。

基本形：

`$folder = "画像フォルダのパス"`

`$names = @(`

`"English_Name_1",`

`"English_Name_2",`

`"English_Name_3"`

`)`

`1..3 | ForEach-Object {`

`    $old = Join-Path $folder "$_.jpg"`

`    $safeName = $names[$_-1] -replace '\s+', '_'`

`    $newName = "WL{0:D3}_{1}.jpg" -f $_, $safeName`

`    if (Test-Path $old) {`

`        Rename-Item -LiteralPath $old -NewName $newName`

`    }`

`}`

実際のリネーム前に、対象ファイルと対応するEnglish_Nameを確認する。

### 5. カバー画像

カバー画像はカード画像とは別に管理する。

形式：

`Deck_ID_cover.拡張子`

例：

`WL_cover.png`

`WO_cover.jpg`

カバー画像にはカード番号を付けない。

### 6. GitHubへ画像をアップロード

リネームが完了したら、作成したデッキフォルダをGitHubで開く。

**Add file → Upload files** を選択する。

リネーム済みのカード画像をまとめてアップロードする。

### 7. フォルダ構成

基本的な構成：

```text
ai-uranai-images/
└─ Deck_ID/
   ├─ Deck_ID_cover.png
   ├─ Deck_ID001_カード名.png
   ├─ Deck_ID002_カード名.png
   └─ …
