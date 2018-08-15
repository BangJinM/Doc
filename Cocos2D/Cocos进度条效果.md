### Cocos 进度条效果

![](pic\Cocos进度条效果.gif)

代码：

```lua

function GameScene:ProgressStripeEffect(time,parent,position,isClockwise)
    local size=cc.p(80,114)
    isClockwise=isClockwise or true
    -- ---------
    -- |A\     |
    -- |  \    |
    -- |  B\   |
    -- |  /C\  |
    -- | /   \ |
    -- |/     \|
    -- ---------
    --求各个角度
    local sinA=size.x/(math.sqrt( size.x *size.x+size.y* size.y)) --求sin(A)
    local angleA=math.asin(sinA) --反三角,求A角度
    local angleB=math.pi-2*angleA
    local angleC=math.pi-angleB

    --创建进度条，进度条类型是绕着中心成扇形消失
    local sprite=cc.Sprite:create("HeFeiMJ/Face/ProgressStripeEffectBack.png")
    local progressBar=cc.ProgressTimer:create(sprite)
  	--local progressBarAction=cc.ProgressTo:create(time,100) --从0到100
    local progressBarAction = cc.ProgressFromTo:create(time, 100,0)  	--从100到0
    if(progressBar)then
        -- 设置进度计时的类型，这里是绕圆心
        progressBar:setType(cc.PROGRESS_TIMER_TYPE_RADIAL)
        -- 设置显示位置
        progressBar:setPosition(cc.p(0,0))
        progressBar:setReverseDirection(isClockwise)
        -- 运行动作
        progressBar:runAction(cc.RepeatForever:create(progressBarAction))
        -- 添加到层当中
        parent:addChild(progressBar)
    end

    --创建粒子效果，粒子跟随消失的点
    local particle=cc.CSLoader:createNodeWithVisibleSize("HeFeiMJ/Face/ProgressStripeEffect.csb")
    local posX=0
    local posY=0
    particle:setPosition(cc.p(posX,posY+size.y/2))

    --创建动画,动画从A->B->C->D->E->A
    --总共分为五个步骤
    --     A 
    --B---------E
    -- | \ |   |
    -- |  \|   |
    -- |   \   |
    -- |  / \  |
    -- | /   \ |
    -- |/     \|
    --C---------D
    local timeAB=angleC/(2*math.pi)/2*time
    local timeBC=angleB/(2*math.pi)*time
    local timeCD=angleC/(2*math.pi)*time
    local tiemDE=angleB/(2*math.pi)*time
    local tiemEA=angleC/(2*math.pi)/2*time

    local sign=1
    if isClockwise ==true then 
        sign=-1
    end

    local actionAB=cc.MoveTo:create(timeAB,cc.p(sign*(posX-size.x/2),posY+size.y/2))
    local actionBC=cc.MoveTo:create(timeBC,cc.p(sign*(posX-size.x/2),posY-size.y/2))
    local actionCD=cc.MoveTo:create(timeCD,cc.p(sign*(posX+size.x/2),posY-size.y/2))
    local actionDE=cc.MoveTo:create(tiemDE,cc.p(sign*(posX+size.x/2),posY+size.y/2))
    local actionEA=cc.MoveTo:create(tiemEA,cc.p(sign*(posX),posY+size.y/2))

    local action=cc.Sequence:create(actionAB,actionBC,actionCD,actionDE,actionEA)
    particle:runAction(action)
    parent:addChild(particle)
end
```

