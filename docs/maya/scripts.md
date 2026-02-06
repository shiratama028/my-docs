## テクスチャが作れない

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


## ma保存できない

string $unknownNodes[] = `lsType unknown`;
 for($node in $unknownNodes){
 if($node=="<done>")
 break;
 if(`objExists $node`){ 
 int $lockState[] = `lockNode -q -l $node`;
 if($lockState[0]==1)
 lockNode -l off $node;
 delete $node;
 }
 } 
 
 ##消せないカメラを消す