```lua
-- 创建 Ping 标签
local pingLabel = Instance.new("TextLabel")
pingLabel.Name = "PingLabel"
pingLabel.Parent = SkK
pingLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
pingLabel.BackgroundTransparency = 1
pingLabel.Position = UDim2.new(0, 10, 0, 160)
pingLabel.Size = UDim2.new(0, 200, 0, 20)
pingLabel.Font = Enum.Font.SourceSans
pingLabel.TextSize = 14
pingLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

-- 创建 FPS 标签
local fpsLabel = Instance.new("TextLabel")
fpsLabel.Name = "FPSLabel"
fpsLabel.Parent = SkK
fpsLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
fpsLabel.BackgroundTransparency = 1
fpsLabel.Position = UDim2.new(0, 10, 0, 190)
fpsLabel.Size = UDim2.new(0, 200, 0, 20)
fpsLabel.Font = Enum.Font.SourceSans
fpsLabel.TextSize = 14
fpsLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

-- 更新函数，实时显示 Ping 和 FPS
local function UpdatePingAndFPS()
    -- 获取当前 Ping 和 FPS
    local ping = game.Stats.PerformanceStats.Ping:GetValue()
    local fps = game.Stats.PerformanceStats.FPS:GetValue()
    
    -- 更新 Ping 和 FPS 标签文本
    pingLabel.Text = "Ping: " .. tostring(ping) .. " ms"
    fpsLabel.Text = "FPS: " .. tostring(fps)
end

-- 初始调用一次更新函数
UpdatePingAndFPS()

-- 每秒调用一次更新函数，实现实时显示
game:GetService("RunService").Heartbeat:Connect(function()
    UpdatePingAndFPS()
end)

-- 创建 FPS 标签
local fpsLabel = Instance.new("TextLabel")
fpsLabel.Name = "FPSLabel"
fpsLabel.Parent = SkK
fpsLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
fpsLabel.BackgroundTransparency = 1
fpsLabel.Position = UDim2.new(0, 10, 0, 190)
fpsLabel.Size = UDim2.new(0, 200, 0, 20)
fpsLabel.Font = Enum.Font.SourceSans
fpsLabel.TextSize = 14
fpsLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

-- 定义 FPS 更新函数
local function UpdateFPS()
    local now = tick()  -- 获取当前时间
    local dt = now - (lastUpdate or now)  -- 计算时间差
    local fps = 1 / dt  -- 计算 FPS
    lastUpdate = now  -- 更新上次更新时间
    
    -- 更新 FPS 标签文本
    fpsLabel.Text = "FPS: " .. tostring(math.floor(fps + 0.5))
end

-- 初始调用一次更新函数
UpdateFPS()

-- 每帧调用一次更新函数，实现实时显示
game:GetService("RunService").RenderStepped:Connect(function()
    UpdateFPS()
end)
```