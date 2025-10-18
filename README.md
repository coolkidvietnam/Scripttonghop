local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
local Window = Rayfield:CreateWindow({
   Name = "sigma GUI 🇻🇳",
   LoadingTitle = "sigma Việt Nam",
   LoadingSubtitle = "By skibidi hecker",
   ConfigurationSaving = {Enabled = false}
})

local Tab1 = Window:CreateTab("Menu Chính", 4483362458)
Tab1:CreateButton({
   Name = "Fly",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/coolkidvietnam/refs/heads/main/Script%20cool%20kid"))()
   end
})
Tab1:CreateButton({
   Name = "VFly (Xe bay)",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostPlayer352/Test4/main/Vehicle%20Fly%20Gui"))()
   end
})
Tab1:CreateInput({
   Name = "Nhập tốc độ chạy",
   PlaceholderText = "Ví dụ: 50",
   RemoveTextAfterFocusLost = false,
   Callback = function(value)
       local speed = tonumber(value)
       if speed then
           local plr = game.Players.LocalPlayer
           local chr = plr.Character or plr.CharacterAdded:Wait()
           local hum = chr:FindFirstChildOfClass("Humanoid")
           if hum then
               hum.WalkSpeed = speed
           end
       end
   end
})
Tab1:CreateButton({
   Name = "Fix Lag",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/Fix-lag/refs/heads/main/C00LKID2K25"))()
   end
})
Tab1:CreateButton({
   Name = "Tàng hình",
   Callback = function()
       loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Invisible-script-20557"))()
   end
})
Tab1:CreateButton({
   Name = "Lọ Vương (Goon)",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/Goon/refs/heads/main/README.md"))()
   end
})
Tab1:CreateButton({
   Name = "Quay ngược thời gian",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/0Ben1/fe./main/L"))()
   end
})
Tab1:CreateButton({
   Name = "đừng nhấn",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/TheqopThe/robax/refs/heads/main/jumpscare.lua"))()
   end
})

local Tab2 = Window:CreateTab("OP", 7743873524)
Tab2:CreateButton({
   Name = "Dupe item đang cầm (Thử nhiều cách)",
   Callback = function()
       local Players = game:GetService("Players")
       local plr = Players.LocalPlayer
       local char = plr.Character or plr.CharacterAdded:Wait()
       local backpack = plr:WaitForChild("Backpack")
       local function notify(title, text, duration)
           pcall(function()
               game:GetService("StarterGui"):SetCore("SendNotification", {
                   Title = title;
                   Text = text;
                   Duration = duration or 4;
               })
           end)
       end
       local tool
       for _,v in ipairs(char:GetChildren()) do
           if v:IsA("Tool") then
               tool = v
               break
           end
       end
       if not tool then
           notify("Dupe", "Không tìm thấy item đang cầm.", 3)
           return
       end
       local name = tool.Name
       local function countInBackpack()
           local c = 0
           for _,v in ipairs(backpack:GetChildren()) do
               if v:IsA("Tool") and v.Name == name then c = c + 1 end
           end
           return c
       end
       local before = countInBackpack()
       local success = false
       pcall(function()
           local c = tool:Clone()
           c.Parent = backpack
           wait(0.25)
           if countInBackpack() > before then success = true end
       end)
       if not success then pcall(function()
           local orig = tool.Parent
           tool.Parent = workspace
           wait(0.25)
           tool.Parent = orig
           wait(0.25)
           if countInBackpack() > before then success = true end
       end) end
       if not success then pcall(function()
           local c = tool:Clone()
           c.Parent = workspace
           wait(0.2)
           c.Parent = backpack
           wait(0.25)
           if countInBackpack() > before then success = true end
       end) end
       if not success then pcall(function()
           local orig = tool.Parent
           tool.Parent = nil
           wait(0.2)
           tool.Parent = backpack
           wait(0.25)
           if countInBackpack() > before then success = true end
       end) end
       if success then
           notify("Dupe", "Thử dupe: Có khả năng thành công. Kiểm tra Backpack.", 4)
       else
           notify("Dupe", "Không thể dupe trong game này.", 4)
       end
   end
})
Tab2:CreateButton({
   Name = "FE (OP)",
   Callback = function()
       loadstring(game:HttpGet("https://gist.github.com/someunknowndude/38cecea5be9d75cb743eac8b1eaf6758/raw"))()
   end
})
