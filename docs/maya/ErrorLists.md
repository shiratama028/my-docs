# よくあるエラー関係

| ModuleNotFoundError | モジュールタイプのスクリプト入れようとするとよくある<br>
モジュールフォルダファイルに記載されてるパスにファイル全部入れるとなんとかなる |
|テクスチャファイルが作れない|https://tm8r.hateblo.jp/entry/2023/05/29/101551<br>
from maya import cmds<br>

def fix_invalid_default_texture_ist():<br>
    default_texture_list = cmds.ls(type="defaultTextureList")<br>
    if not default_texture_list:<br>
        return<br>

    default_texture_list = default_texture_list[0]<br>
    if not cmds.lockNode(default_texture_list, q=True, lu=True)[0]:<br>
        return<br>

    cmds.lockNode(default_texture_list, l=False, lu=False)<br><br>

fix_invalid_default_texture_ist()|

|------|------|---------|
| 価格 | 有料 | 無料 |
| 用途 | 業務向け | 個人〜業務 |