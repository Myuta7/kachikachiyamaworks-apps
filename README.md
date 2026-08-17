# kachikachiyamaworks-apps

株式会社カチカチヤマワークスのアプリサポートサイト。GitHub Pages で
**https://apps.kachikachiyamaworks.com/** として公開している。

App Store / Google Play に登録する **サポートURL・プライバシーポリシーURL・
デベロッパWebサイト** はすべてここを指す。アプリ内の「CSVの作り方」リンクも同じ。

## 構成

```
/
├── CNAME                          カスタムドメイン（apps.kachikachiyamaworks.com）
├── .nojekyll                      Jekyll のビルドを止める（素の静的ファイルとして配信）
├── app-ads.txt                    AdMob の販売者認証。**ドメイン直下でないと読まれない**
├── index.html                     アプリ一覧。デベロッパWebサイトの入口
├── assets/style.css               全ページ共通のスタイル
└── tanadoko/
    ├── index.html                 サポートの入口（App Store のサポートURL）
    ├── privacy.html               プライバシーポリシー
    ├── csv-guide.html             取り込むCSVの作り方
    └── tanadoko_template.csv      テンプレート（UTF-8 BOM付き。Excelでそのまま開ける）
```

## 触るときの注意

- **URLを変えない。** ストア側に登録済みで、変更するとアプリの再ビルドと
  ストア審査のやり直しが要る。ページを増やすのは自由。
- **`app-ads.txt` はドメイン直下から動かさない。** サブディレクトリに置くと
  AdMob のクローラが見つけられない。中身の `pub-` は AdMob のパブリッシャーIDで、
  アプリを増やしても1行のままでよい（アカウント単位のため）。
- **プライバシーポリシーは広告SDKを増減したら必ず直す。**
  App Store Connect の「Appのプライバシー」の申告と食い違わせないこと。
- ビルド工程は無い。プッシュすればそのまま配信される（反映まで1分程度）。

## 対応するアプリ側の設定

| 場所 | 値 |
|---|---|
| `lib/services/app_links.dart` の `csvGuide` | https://apps.kachikachiyamaworks.com/tanadoko/csv-guide.html |
| `lib/services/app_links.dart` の `privacyPolicy` | https://apps.kachikachiyamaworks.com/tanadoko/privacy.html |
| ASC サポートURL | https://apps.kachikachiyamaworks.com/tanadoko/ |
| ASC プライバシーポリシーURL | https://apps.kachikachiyamaworks.com/tanadoko/privacy.html |
| ASC マーケティングURL | https://apps.kachikachiyamaworks.com/ |
