# よくあるエラー関係

| エラー | 対処 |
|-------|------|
| ModuleNotFoundError | モジュールタイプのスクリプト入れようとするとよくある<br>モジュールフォルダファイルに記載されてるパスにファイル全部入れるとなんとかなる |
|テクスチャファイルが作れない|https://tm8r.hateblo.jp/entry/2023/05/29/101551<br><pre><code class="language-python">
from maya import cmds

def fix_invalid_default_texture_list():
    default_texture_list = cmds.ls(type="defaultTextureList")
    if not default_texture_list:
        return

    default_texture_list = default_texture_list[0]
    if not cmds.lockNode(default_texture_list, q=True, lu=True)[0]:
        return

    cmds.lockNode(default_texture_list, l=False, lu=False)

fix_invalid_default_texture_list()
</code></pre> |

|------|------|---------|
| 価格 | 有料 | 無料 |
| 用途 | 業務向け | 個人〜業務 |