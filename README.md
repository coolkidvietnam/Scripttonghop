local function loadGUI()
    local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
    ScreenGui.Name = "CoolKidGui"

    local MainFrame = Instance.new("Frame", ScreenGui)
    MainFrame.Size = UDim2.new(0, 500, 0, 350)
    MainFrame.Position = UDim2.new(0.5, -250, 0.5, -175)
    MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    MainFrame.Active = true
    MainFrame.Draggable = true
    MainFrame.Name = "MainFrame"

    local ToggleButton = Instance.new("TextButton", ScreenGui)
    ToggleButton.Size = UDim2.new(0, 120, 0, 35)
    ToggleButton.Position = UDim2.new(0, 10, 1, -10)
    ToggleButton.AnchorPoint = Vector2.new(0, 1)
    ToggleButton.BackgroundColor3 = Color3.fromRGB(90, 90, 90)
    ToggleButton.TextColor3 = Color3.new(1, 1, 1)
    ToggleButton.Text = "Ẩn / Hiện GUI"
    local isVisible = true
    ToggleButton.MouseButton1Click:Connect(function()
        isVisible = not isVisible
        MainFrame.Visible = isVisible
    end)

    local TabButtons = Instance.new("Frame", MainFrame)
    TabButtons.Size = UDim2.new(1, 0, 0, 40)
    TabButtons.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

    local Tabs = {"Menu Chính", "Troll", "Người tạo script"}
    local TabFrames = {}

    for i, name in ipairs(Tabs) do
        local button = Instance.new("TextButton", TabButtons)
        button.Size = UDim2.new(0, 150, 0, 40)
        button.Position = UDim2.new(0, (i - 1) * 160, 0, 0)
        button.Text = name
        button.TextColor3 = Color3.new(1, 1, 1)
        button.BackgroundColor3 = Color3.fromRGB(70, 70, 70)

        local frame = Instance.new("Frame", MainFrame)
        frame.Size = UDim2.new(1, 0, 1, -40)
        frame.Position = UDim2.new(0, 0, 0, 40)
        frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
        frame.Visible = i == 1
        TabFrames[name] = frame

        button.MouseButton1Click:Connect(function()
            for _, f in pairs(TabFrames) do
                f.Visible = false
            end
            frame.Visible = true
        end)
    end

    local function createButton(parent, text, position, callback)
        local button = Instance.new("TextButton", parent)
        button.Size = UDim2.new(0, 150, 0, 40)
        button.Position = position
        button.Text = text
        button.TextColor3 = Color3.new(1, 1, 1)
        button.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
        button.MouseButton1Click:Connect(callback)
    end

    local MainTab = TabFrames["Menu Chính"]
    createButton(MainTab, "Fly", UDim2.new(0, 20, 0, 20), function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/coolkidvietnam/refs/heads/main/Script%20cool%20kid"))()
    end)

    createButton(MainTab, "VFly", UDim2.new(0, 190, 0, 20), function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostPlayer352/Test4/main/Vehicle%20Fly%20Gui"))()
    end)

    local speeds = {16, 25, 50}
    for i, spd in ipairs(speeds) do
        createButton(MainTab, "Tốc độ " .. spd, UDim2.new(0, 20 + (i - 1) * 170, 0, 80), function()
            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = spd
        end)
    end

    createButton(MainTab, "Tốc độ 75", UDim2.new(0, 20, 0, 130), function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 75
    end)

    local TrollTab = TabFrames["Troll"]
    createButton(TrollTab, "Goon", UDim2.new(0, 20, 0, 20), function()
        loadstring(game:HttpGet("https://pastefy.app/wa3v2Vgm/raw"))("Spider Script")
    end)

    local CreatorTab = TabFrames["Người tạo script"]
    local avatar = Instance.new("ImageLabel", CreatorTab)
    avatar.Size = UDim2.new(0, 100, 0, 100)
    avatar.Position = UDim2.new(0, 20, 0, 20)
    avatar.BackgroundTransparency = 1
    avatar.Image = "https://www.roblox.com/headshot-thumbnail/image?userId=8166408827&width=420&height=420&format=png"

    local label = Instance.new("TextLabel", CreatorTab)
    label.Size = UDim2.new(1, -140, 0, 50)
    label.Position = UDim2.new(0, 130, 0, 40)
    label.Text = "ID TikTok: trn.minh.tr0089"
    label.TextColor3 = Color3.new(1, 1, 1)
    label.BackgroundTransparency = 1
    label.TextSize = 20
end

local function createKeyCheck()
    local KeyUI = Instance.new("ScreenGui", game.CoreGui)
    local Frame = Instance.new("Frame", KeyUI)
    Frame.Size = UDim2.new(0, 400, 0, 200)
    Frame.Position = UDim2.new(0.5, -200, 0.5, -100)
    Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    Frame.Active = true
    Frame.Draggable = true

    local label = Instance.new("TextLabel", Frame)
    label.Size = UDim2.new(1, 0, 0, 50)
    label.Text = "Hoàng Sa và Trường Sa là của nước nào?"
    label.TextColor3 = Color3.new(1, 1, 1)
    label.BackgroundTransparency = 1
    label.TextSize = 20

    local btnVN = Instance.new("TextButton", Frame)
    btnVN.Size = UDim2.new(0, 150, 0, 40)
    btnVN.Position = UDim2.new(0, 30, 0, 100)
    btnVN.Text = "Việt Nam"
    btnVN.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    btnVN.TextColor3 = Color3.new(1, 1, 1)
    btnVN.MouseButton1Click:Connect(function()
        KeyUI:Destroy()
        loadGUI()
    end)

    local btnCN = Instance.new("TextButton", Frame)
    btnCN.Size = UDim2.new(0, 150, 0, 40)
    btnCN.Position = UDim2.new(0, 220, 0, 100)
    btnCN.Text = "Trung Quốc"
    btnCN.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
    btnCN.TextColor3 = Color3.new(1, 1, 1)
    btnCN.MouseButton1Click:Connect(function()
        game.Players.LocalPlayer:Kick("Bạn đã chọn sai.")
    end)
end

createKeyCheck()
