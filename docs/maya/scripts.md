## テクスチャが作れない

from maya import cmds

def fix_invalid_default_texture_ist():<br>
　default_texture_list = cmds.ls(type="defaultTextureList")<br>
　if not default_texture_list:<br>
　　　return<br>

　default_texture_list = default_texture_list[0]<br>
　if not cmds.lockNode(default_texture_list, q=True, lu=True)[0]:<br>
　　　return<br>

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
 
 ## 消せないカメラを消す
 対象のカメラを選択して下記を実行
 
 string $selection[] = `ls -sl -dag -type camera`;  
string $cameras[]; 
for ($each in $selection) 
{ 
if(`objectType -isType "camera" $each`) 
{ 
$cameras[(size($cameras))] = $each; 
camera -e -startupCamera false $each; 
delete $each; 
} 
else 
{ 
warning("selected object isn't a camera"); 
} 
};

 