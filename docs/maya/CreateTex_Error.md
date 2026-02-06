from maya import cmds

def fix_invalid_default_texture_ist():
    default_texture_list = cmds.ls(type="defaultTextureList")
    if not default_texture_list:
        return

    default_texture_list = default_texture_list[0]
    if not cmds.lockNode(default_texture_list, q=True, lu=True)[0]:
        return

    cmds.lockNode(default_texture_list, l=False, lu=False)

fix_invalid_default_texture_ist()