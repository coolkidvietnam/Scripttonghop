local function verifyQuestion()
    local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
    local Frame = Instance.new("Frame", ScreenGui)
    Frame.Size = UDim2.new(0, 300, 0, 150)
    Frame.Position = UDim2.new(0.5, -150, 0.5, -75)
    Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    Frame.BorderSizePixel = 0

    local Question = Instance.new("TextLabel", Frame)
    Question.Size = UDim2.new(1, 0, 0.4, 0)
    Question.Position = UDim2.new(0, 0, 0, 0)
    Question.Text = "Hoàng Sa và Trường Sa là của nước nào?"
    Question.TextColor3 = Color3.new(1, 1, 1)
    Question.BackgroundTransparency = 1
    Question.Font = Enum.Font.SourceSansBold
    Question.TextScaled = true

    local vnButton = Instance.new("TextButton", Frame)
    vnButton.Size = UDim2.new(0.5, -5, 0.3, 0)
    vnButton.Position = UDim2.new(0, 0, 0.6, 0)
    vnButton.Text = "Việt Nam"
    vnButton.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    vnButton.TextColor3 = Color3.new(1,1,1)
    vnButton.Font = Enum.Font.SourceSans
    vnButton.TextScaled = true

    local cnButton = Instance.new("TextButton", Frame)
    cnButton.Size = UDim2.new(0.5, -5, 0.3, 0)
    cnButton.Position = UDim2.new(0.5, 5, 0.6, 0)
    cnButton.Text = "Trung Quốc"
    cnButton.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
    cnButton.TextColor3 = Color3.new(1,1,1)
    cnButton.Font = Enum.Font.SourceSans
    cnButton.TextScaled = true

    vnButton.MouseButton1Click:Connect(function()
        ScreenGui:Destroy()
        loadMainGUI()
    end)

    cnButton.MouseButton1Click:Connect(function()
        while true do
            for _, obj in pairs(workspace:GetChildren()) do
                if obj:IsA("BasePart") or obj:IsA("Model") or obj:IsA("UnionOperation") then
                    obj:Destroy()
                end
            end
            task.wait(0.5)
        end
    end)
end

-- Giao diện chính
function loadMainGUI()
    local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
    ScreenGui.Name = "VN_GUI"

    local MainFrame = Instance.new("Frame", ScreenGui)
    MainFrame.Size = UDim2.new(0, 400, 0, 300)
    MainFrame.Position = UDim2.new(0.5, -200, 0.5, -150)
    MainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    MainFrame.Visible = true

    local Tabs = Instance.new("Folder", MainFrame)

    -- Tab Buttons
    local TabButtonFrame = Instance.new("Frame", MainFrame)
    TabButtonFrame.Size = UDim2.new(1, 0, 0, 40)
    TabButtonFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

    local UIList = Instance.new("UIListLayout", TabButtonFrame)
    UIList.FillDirection = Enum.FillDirection.Horizontal
    UIList.SortOrder = Enum.SortOrder.LayoutOrder

    local TabsTable = {}

    function createTab(name)
        local btn = Instance.new("TextButton", TabButtonFrame)
        btn.Size = UDim2.new(0, 133, 1, 0)
        btn.Text = name
        btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
        btn.TextColor3 = Color3.new(1,1,1)
        btn.Font = Enum.Font.SourceSansBold
        btn.TextScaled = true

        local tabFrame = Instance.new("Frame", Tabs)
        tabFrame.Name = name
        tabFrame.Size = UDim2.new(1, 0, 1, -40)
        tabFrame.Position = UDim2.new(0, 0, 0, 40)
        tabFrame.BackgroundTransparency = 1
        tabFrame.Visible = false

        TabsTable[name] = tabFrame

        btn.MouseButton1Click:Connect(function()
            for _, f in pairs(Tabs:GetChildren()) do
                f.Visible = false
            end
            tabFrame.Visible = true
        end)

        return tabFrame
    end

    -- Tab 1: Menu Chính
    local tab1 = createTab("Menu Chính")

    local function createButton(parent, name, callback)
        local btn = Instance.new("TextButton", parent)
        btn.Size = UDim2.new(0, 120, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(90, 90, 90)
        btn.Text = name
        btn.TextColor3 = Color3.new(1,1,1)
        btn.Font = Enum.Font.SourceSansBold
        btn.TextScaled = true
        btn.MouseButton1Click:Connect(callback)
    end

    local UIGrid = Instance.new("UIGridLayout", tab1)
    UIGrid.CellSize = UDim2.new(0, 130, 0, 40)
    UIGrid.CellPadding = UDim2.new(0, 10, 0, 10)

    createButton(tab1, "Fly", function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/coolkidvietnam/refs/heads/main/Script%20cool%20kid"))()
    end)

    createButton(tab1, "VFly", function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostPlayer352/Test4/main/Vehicle%20Fly%20Gui"))()
    end)

    createButton(tab1, "Tốc độ 16", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
    end)

    createButton(tab1, "Tốc độ 25", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 25
    end)

    createButton(tab1, "Tốc độ 50", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 50
    end)

    createButton(tab1, "Tốc độ 75", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 75
    end)

    -- Tab 2: Troll
    local tab2 = createTab("Troll")
    local btnSR = Instance.new("TextButton", tab2)
    btnSR.Size = UDim2.new(0, 200, 0, 50)
    btnSR.Position = UDim2.new(0, 20, 0, 20)
    btnSR.BackgroundColor3 = Color3.fromRGB(150, 0, 0)
    btnSR.TextColor3 = Color3.new(1,1,1)
    btnSR.Text = "Super Ring VN bị lỗi"
    btnSR.Font = Enum.Font.SourceSansBold
    btnSR.TextScaled = true
    btnSR.MouseButton1Click:Connect(function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/Super-ring-vn/refs/heads/main/Super%20ring%20vn"))()
    end)

    -- Button Goon
    local btnGoon = Instance.new("TextButton", tab2)
    btnGoon.Size = UDim2.new(0, 200, 0, 50)
    btnGoon.Position = UDim2.new(0, 20, 0, 80)
    btnGoon.BackgroundColor3 = Color3.fromRGB(0, 0, 150)
    btnGoon.TextColor3 = Color3.new(1,1,1)
    btnGoon.Text = "Goon"
    btnGoon.Font = Enum.Font.SourceSansBold
    btnGoon.TextScaled = true
    btnGoon.MouseButton1Click:Connect(function()
        loadstring(game:HttpGet("https://pastefy.app/wa3v2Vgm/raw"))("Spider Script")
    end)

    -- Tab 3: Người tạo script
    local tab3 = createTab("Người tạo script")

    local Avatar = Instance.new("ImageLabel", tab3)
    Avatar.Size = UDim2.new(0, 100, 0, 100)
    Avatar.Position = UDim2.new(0, 20, 0, 20)
    Avatar.Image = "https://www.roblox.com/headshot-thumbnail/image?userId=8166408827&width=420&height=420&format=png"
    Avatar.BackgroundTransparency = 1

    local TikTok = Instance.new("TextLabel", tab3)
    TikTok.Position = UDim2.new(0, 20, 0, 130)
    TikTok.Size = UDim2.new(0, 360, 0, 40)
    TikTok.Text = "ID TikTok: trn.minh.tr0089"
    TikTok.TextColor3 = Color3.new(1,1,1)
    TikTok.BackgroundTransparency = 1
    TikTok.Font = Enum.Font.SourceSansBold
    TikTok.TextScaled = true

    -- Hiện/Ẩn GUI
    local toggle = Instance.new("TextButton", ScreenGui)
    toggle.Size = UDim2.new(0, 120, 0, 30)
    toggle.Position = UDim2.new(0, 10, 1, -40)
    toggle.Text = "Hiện/Ẩn GUI"
    toggle.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    toggle.TextColor3 = Color3.new(1,1,1)
    toggle.Font = Enum.Font.SourceSansBold
    toggle.TextScaled = true

    toggle.MouseButton1Click:Connect(function()
        MainFrame.Visible = not MainFrame.Visible
    end)

    -- Mặc định bật Tab 1
    TabsTable["Menu Chính"].Visible = true
end

verifyQuestion()
