local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
local Window = Rayfield:CreateWindow({
   Name = "CoolKid GUI 🇻🇳",
   LoadingTitle = "CoolKid Việt Nam",
   LoadingSubtitle = "By trn.minh.tr0089",
   ConfigurationSaving = {Enabled = false}
})
local Tab = Window:CreateTab("Menu Chính", 4483362458)
Tab:CreateButton({
   Name = "Fly",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/coolkidvietnam/refs/heads/main/Script%20cool%20kid"))()
   end
})
Tab:CreateButton({
   Name = "VFly (Xe bay)",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/GhostPlayer352/Test4/main/Vehicle%20Fly%20Gui"))()
   end
})
Tab:CreateSlider({
   Name = "Tốc độ chạy",
   Range = {16, 200},
   Increment = 1,
   Suffix = "WalkSpeed",
   CurrentValue = 16,
   Flag = "SpeedSlider",
   Callback = function(value)
       local plr = game.Players.LocalPlayer
       local chr = plr.Character or plr.CharacterAdded:Wait()
       local hum = chr:FindFirstChildOfClass("Humanoid")
       if hum then
           hum.WalkSpeed = value
       end
   end
})
Tab:CreateButton({
   Name = "Fix Lag",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/Fix-lag/refs/heads/main/C00LKID2K25"))()
   end
})
Tab:CreateButton({
   Name = "Tàng hình",
   Callback = function()
       loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Invisible-script-20557"))()
   end
})
Tab:CreateButton({
   Name = "Lọ Vương (Goon)",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/coolkidvietnam/Goon/refs/heads/main/README.md"))()
   end
})
Tab:CreateButton({
   Name = "Quay ngược thời gian",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/0Ben1/fe./main/L"))()
   end
})
Tab:CreateButton({
   Name = "đừng nhấn",
   Callback = function()
       loadstring(game:HttpGet("https://raw.githubusercontent.com/TheqopThe/robax/refs/heads/main/jumpscare.lua"))()
   end
})
