# メタプロンプト抽出ツール（ブラウザ完結）

ComfyUI / A1111(Forge) で生成したPNGに埋め込まれたメタプロンプトから、**ポジティブプロンプトだけ**を抜き出すブラウザD&Dツールです。

- **サーバー不要・インストール不要**：公開URLを開くだけ
- **画像は端末から一切送信されません**（すべてブラウザ内で完結）

## 使い方
1. 公開URLを開く
2. 画像を画面にドラッグ＆ドロップ（複数まとめてOK）
3. ポジティブプロンプトが表示される → **コピー** / **CSVダウンロード**
4. 「✨ 1行に整形（カンマ区切り）」で改行をカンマ区切りに変換

## 対応している埋め込み
- **ComfyUI**: PNGの `prompt` チャンク(API JSON)を解析。KSampler系の `positive` 入力をたどり、`ConditioningConcat` / `PromptSwitch` / `CLIPTextEncode` を再帰的に組み立て。`//` で無効化された行は自動除去。
- **A1111 / Forge**: `parameters` チャンクの "Negative prompt:" より前を抽出。

zTXt/iTXt圧縮メタにも対応（modern Edge/Chrome の DecompressionStream を使用）。
