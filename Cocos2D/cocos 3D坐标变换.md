cocos 3D坐标变换

```

-- 世界空间->摄像机空间->屏幕点
-- @param pos 世界坐标
-- @param camera 摄像机
-- @return 屏幕坐标
function ToolUtils.CameraPos2screenPos(pos,camera)
    local screenSize=cc.Director:getInstance():getWinSize()
    if camera then
        local newpos = camera:project(pos) 
        newpos.y = screenSize.height - newpos.y
        return newpos
    end
end

-- 获得3D节点的世界坐标
-- @param node节点
-- @param 世界坐标
function ToolUtils.getWorldPosition(node)--手牌相机3d空间点到屏幕点
    local parent = node:getParent()
    local pos = node:getPosition3D()
    local t = parent:getNodeToWorldTransform()
end

-- 坐标变换 
-- @param pos 3维坐标
-- @param t 仿射变换矩阵
-- @return 变换后的坐标
function ToolUtils.vec3Transform(pos, t)
    local new = cc.vec3(0,0,0)
    new.x = pos.x * t[1] + pos.y * t[5] +  pos.z * t[9]+ t[13]
    new.y = pos.x * t[2] + pos.y * t[6] +  pos.z * t[10]+ t[14]
    new.z = pos.x * t[3] + pos.y * t[7] +  pos.z * t[11]+ t[15]
    return new
end
```

