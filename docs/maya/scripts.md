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

string $unknownNodes[] = `lsType unknown`;<br>
 for($node in $unknownNodes){<br>
 if($node=="<done>")<br>
 break;<br>
 if(`objExists $node`){ <br>
 int $lockState[] = `lockNode -q -l $node`;<br>
 if($lockState[0]==1)<br>
 lockNode -l off $node;<br>
 delete $node;<br>
 }<br>
 } <br>
 
 ## 消せないカメラを消す
 対象のカメラを選択して下記を実行
 
 string $selection[] = `ls -sl -dag -type camera`;<br>
string $cameras[];<br>
for ($each in $selection)<br>
{<br>
if(`objectType -isType "camera" $each`)<br>
{<br>
$cameras[(size($cameras))] = $each;<br>
camera -e -startupCamera false $each;<br>
delete $each;<br>
}<br>
else<br>
{<br>
warning("selected object isn't a camera");<br>
}<br>
};<br>
 