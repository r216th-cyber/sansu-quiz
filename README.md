# さんすうクイズ 〜ちょうちょをあつめよう〜

1ねんせい向けのたしざん・ひきざんクイズ。クリアするとちょうちょが集められて、毎日遊ぶと虫かごの幼虫が育ちます。

## 遊ぶ

https://r216th-cyber.github.io/sansu-quiz/

iPhone / Android では Safari・Chrome で開いて「ホーム画面に追加」するとアプリとして使えます(オフラインでも動作)。

## ファイル構成

- `sansu-quiz.html` — アプリ本体(編集はこのファイルに対して行う)
- `pwa-head.html` / `pwa-tail.html` — PWA用のヘッダー・フッター
- `index.html` — 公開用(上記3ファイルを連結して生成する。直接編集しない)
- `sw.js` — Service Worker(オフラインキャッシュ)。`index.html` を更新したら中の `CACHE` のバージョン番号を上げること
- `manifest.webmanifest` / `icon-*.png` — アプリのアイコンなど

`index.html` の再生成(PowerShell):

```powershell
$u8 = [System.Text.UTF8Encoding]::new($false)
$dir = "."
[System.IO.File]::WriteAllText("$dir\index.html",
  [System.IO.File]::ReadAllText("$dir\pwa-head.html", $u8) +
  [System.IO.File]::ReadAllText("$dir\sansu-quiz.html", $u8) +
  [System.IO.File]::ReadAllText("$dir\pwa-tail.html", $u8), $u8)
```
