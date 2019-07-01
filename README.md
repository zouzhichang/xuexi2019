# xuexi2019
学习强国
Delay 2000
Dim screenX,screenY,deviceID,first=25
screenX = GetScreenX()
screenY = GetScreenY()
deviceID = GetDeviceID()
TracePrint ""&screenX&"*"&screenY&chr(10)
call messagebox ("御坂脚本，启动！")

Dim yisepinci,fengxiang,i,b,d,c//如果为1则执行评价功能,b为设置评论次数//
yisepinci = 1
fengxiang = 1
b = 1
d = 1
Touch 1239,365, 100//点中间学习图标//
Delay 1000
Touch 147,375, 100//再点推荐//
Delay 1000
While first>0
    call messagebox ("准备点击文章")
    TracePrint "准备点击文章"
    Call dianwen()
    first = first - 1
    TouchDown 1010,350,1
    TouchMove 500,370,1,400
    TouchUp 1
    Delay 3000
Wend
//----------------//
Sub dianwen()
    

    Touch 631,345, 100//点击文章，进入文章//
    Delay 1000
    TracePrint "进入文章"//进入文章内部后慢慢下滑10S，点击收藏，点击评论归零，长按第一个评论，复制，点击，粘贴，发布，点击左上角返回//
    call messagebox ("进入文章")
    Delay 1000
    call messagebox ("下滑10次")
    TracePrint "缓慢下滑10次"
    For i = 1 To 10 Step 1//缓慢下滑10次//
        TouchDown 1013,366, 1
        TouchMove 643,371, 1, 400
        TouchUp 1
    call messagebox ("滑动一次")
        Delay 2000
    Next
    call messagebox ("点击收藏")
    Touch 1244,113, 100
    Delay 1000
    If yisepinci = 1 And b < 5 Then 
        Call pingjia()
        b=b+1
    End If
    Delay 1000
    If fengxiang = 1 And d < 5 Then 
        Call fx()
        d=d+1
    End If
    call messagebox ("返回主界面")//返回主界面，完成一次文章查看//
    Touch 76,676, 100
    Delay 2000

    
End Sub

//----------------//
Sub messagebox(box)
    TracePrint box
    ShowMessage box
    Delay 1500
End Sub

//---评价子程序---//
Sub pingjia()
    

    call messagebox ("点击评论，回到第一个评论位置")
    Touch 1249,207, 100
    Delay 1000
    call messagebox ("点击输入框，获得光标")
    Touch 1249,500, 100
    Delay 1000
    c = Int((5 - 1+1) * Rnd() + 1)//产生一个5至1之间的随机数//
    Select Case c//判断随机数//
    Case 2
        InputText "变则通，通则变，改变方式，提升效益，创新引领中国发展！"//情况1
    Case 3
        InputText "根植历史，放眼未来，创建美丽文明中国！"//情况2
    Case 4
        InputText "友谊天长地久，加强交流，增加合作，共同创新，共建未来！"//情况2
    Case 5
        InputText "开放，包容，建设人类命运共同体的光明前景！"//情况2
    Case Else
        InputText "祝愿祖国目前繁荣昌盛，国泰民安！"//否则
    End Select
    Delay 1000
    call messagebox ("点击发表")
    Touch 1167,53, 100
    Delay 1000
    
End Sub

//---分享子程序---//
Sub fx()
    
    messagebox ("点击分享")//点击分享，点分享到学习强国，点击群，点发送//
    Touch 1244,50, 100
    Delay 1000
    messagebox ("点分享到学习强国")//点分享到学习强国//
    Touch 880,633, 100
    Delay 1000
    messagebox ("点击群")//点击群//
    Touch 470,355, 100
    Delay 1000
    messagebox ("点发送")//点发送，坐标未确定//
    Touch 775,145, 100
    Delay 2000
    
End Sub
