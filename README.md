# 上高野バス 平日ダイヤ（PWA）

上高野⇄京大エリアの市バス31/65号系統・平日ダイヤを、スマホで使えるPWAにしたものです。
ダークテーマ、行き／帰りのトグル切替、オフライン表示に対応しています。

## 含まれるファイル
- `index.html` … アプリ本体
- `manifest.webmanifest` … PWA定義（名前・アイコン・表示モード）
- `sw.js` … Service Worker（オフライン用キャッシュ）
- `icon-192.png` / `icon-512.png` / `icon-maskable-512.png` … アイコン

## GitHub Pages で公開する

```bash
# このフォルダ内で
git init
git add .
git commit -m "bus timetable PWA"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/<リポジトリ名>.git
git push -u origin main
```

GitHub のリポジトリ → Settings → Pages → Source を `main` ブランチ（`/root`）に設定。
数十秒後、`https://<ユーザー名>.github.io/<リポジトリ名>/` で公開されます。
（PWA・Service Worker には HTTPS が必要ですが、GitHub Pages は標準でHTTPSです）

すべて相対パスにしてあるので、リポジトリ名がサブパスになっても動きます。

## スマホにインストール
- iPhone（Safari）：共有ボタン →「ホーム画面に追加」
- Android（Chrome）：メニュー →「アプリをインストール」

インストール後はアイコンから全画面で起動し、オフラインでも開けます。

## ダイヤを更新したとき
1. `index.html` の `DATA` を書き換える
2. `sw.js` の `const CACHE = 'kamitakano-bus-v1'` の番号を `v2` などに上げる
3. push する（番号を上げると古いキャッシュが破棄され、確実に最新が反映されます）

## 出典・注意
- 京都市交通局の時刻表（2026年3月20日改正）にもとづく平日ダイヤです。お盆・年末年始を除きます。
- 到着時刻は各停留所の時刻表どうしを突き合わせた目安で、道路状況により前後します。
