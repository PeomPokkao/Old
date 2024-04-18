local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Patskorn/GUI/main/Copy-SynapOver.lua"))()

local GUI = library:new("Pokkao Hub "," Premium Scripts ]")
local Tab1 = GUI:Tap("Genaral")
local Tab2 = GUI:Tap("Teleport")
local Tab3 = GUI:Tap("RTX GRAPHICS")
local Tab4 = GUI:Tap("others")
local Tab5 = GUI:Tap("Visuals")
local Tab6 = GUI:Tap("credits")
local Tab7 = GUI:Tap("CODE-REDEEM")

function CheckLevel()
    local lv = game:GetService("Players").LocalPlayer.Data.Level.Value
    if lv == 1 or lv <= 9 then
        PosPuk = CFrame.new(1192.56, 17.0468, 1616.61)
        PosQ = CFrame.new(1059.37195, 17.9649925, 1550.42371, 0.939700544, -0, -0.341998369, 0, 1, -0, 0.341998369, 0, 0.939700544)
        Mon = "Bandit [Lv. 5]"
        QuestName = "BanditQuest1"
        QuestNumber = 1
        NameMon = "Bandits"
    elseif lv == 10 or lv <= 14 then
        PosPuk = CFrame.new(-1538.796142578125, 36.39720916748047, 51.27644348144531)
        PosQ = CFrame.new(-1600.123291015625, 37.19538497924805, 153.33087158203125)
        Mon = "Monkey [Lv. 14]"
        QuestName = "JungleQuest"
        QuestNumber = 1
        NameMon = "Monkey"
    elseif lv == 15 or lv <= 29 then
        PosPuk = CFrame.new(-1325.962646484375, 6.450259685516357, -622.9647827148438)
        PosQ = CFrame.new(-1600.123291015625, 37.19538497924805, 153.33087158203125)
        Mon = "Gorilla [Lv. 20]"
        QuestName = "JungleQuest"
        QuestNumber = 2
        NameMon = "Gorilla"
    end
end
CheckLevel()

function CheckMelee()
    for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
        if v.ToolTip == "Melee" then
            _G.Weapon = v.Name
        end
     end
 end
 CheckMelee()
 
 function EquipTool(Tool)
     local lol = game.Players.LocalPlayer.Backpack:FindFirstChild(Tool)
     
     game.Players.LocalPlayer.Character.Humanoid:EquipTool(lol)
 end

function QuestVis()
    return game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible
end

function TP2(P1)
    local Dis = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    local Speed
    if Dis < 1000 then
        Speed = 300
    elseif Dis >= 100 then
        Speed = 200
    end
    local tween = game:GetService("TweenService"):Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart,TweenInfo.new(Dis/Speed,Enum.EasingStyle.Linear),{CFrame = P1})
    tween:Play()
	_G.Part = true
end

Tab2:Dropdown("Teleport in world 1",{"PirateDefault", "Jungle", "central island", "sand island", "Pirate Land", "iceland", "Prison", "Marine Land", "Colosseum", "LV.600+ LAND", "undersea city", "Marine Defauit"},function(t)
    _G.Teleport = t
end)

Tab2:Line()

Tab2:Button("Tween",function(value)
    pcall(function()
        if _G.Teleport == "PirateDefault" then
            TP2(CFrame.new(1020.9113159179688, 95.82339477539062, 1567.62890625))
        elseif _G.Teleport == "Jungle" then
             TP2(CFrame.new(-1608.33447265625, 12.052069664001465, 144.2525634765625))
         elseif _G.Teleport == "central island" then
             TP2(CFrame.new(-784.29248046875, 33.65190124511719, 1606.9835205078125))
         elseif
             _G.Teleport == "sand island" then
            TP2(CFrame.new(1330.142333984375, 101.86573791503906, 4489.53955078125)) 
             elseif
              _G.Teleport == "Pirate Land" then
            TP2(CFrame.new(-1252.4139404296875, 44.55205535888672, 3820.52392578125)) 
              elseif
              _G.Teleport == "iceland" then
            TP2(CFrame.new(1222.4112548828125, 70.81449127197266, -1243.112548828125)) 
              elseif
              _G.Teleport == "Prison" then
            TP2(CFrame.new(5010.4150390625, 88.6519775390625, 738.5647583007812)) 
              elseif
              _G.Teleport == "Marine Land" then
            TP2(CFrame.new(-5150.67724609375, 375.9053649902344, 4443.45654296875)) 
              elseif
              _G.Teleport == "Colosseum" then
            TP2(CFrame.new(-1829.173583984375, 80.37115478515625, -3054.580810546875)) 
              elseif
              _G.Teleport == "LV.600+ LAND" then
            TP2(CFrame.new(5052.1962890625, 48.429481506347656, 4057.39306640625)) 
              elseif
              _G.Teleport == "undersea city" then
            TP2(CFrame.new(4049.18798828125, 1.9886010885238647, -1815.5950927734375)) 
              elseif
              _G.Teleport == "comeback undersea city" then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))))
         elseif     _G.Teleport == "Marine Defauit" then
            TP2(CFrame.new(61169.515625, 1.6770490407943726, 1953.4300537109375)) 
         else
            StopTween(_G.Teleport)
         end
    end)
end)

Tab2:Button("Stop Tween",function(value)
    pcall(function()
        TP2(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
		_G.Part = false
    end)
end)




spawn(function()
    pcall(function()
       game:GetService("RunService").Heartbeat:Connect(function()
        if _G.Part then
          if not game:GetService("Workspace"):FindFirstChild("LOL") then
             local Paertaiteen = Instance.new("Part")
             Paertaiteen.Name = "LOL"
             Paertaiteen.Parent = game.Workspace
             Paertaiteen.Anchored = true
             Paertaiteen.Transparency = 1
             Paertaiteen.Size = Vector3.new(15,0.5,15)
             Paertaiteen.Material = "Neon"
             while true do 
                 wait(0.1) 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 155, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 155, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 155)}):Play() 
                 wait(.5)
             end 
         elseif game:GetService("Workspace"):FindFirstChild("LOL") then
             game.Workspace["LOL"].CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Y - 3.92,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
         end
     else
         if game:GetService("Workspace"):FindFirstChild("LOL") then
             game:GetService("Workspace"):FindFirstChild("LOL"):Destroy()
         end
        end
    end)
 end)
end)



local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Patskorn/GUI/main/Copy-SynapOver.lua"))()

local GUI = library:new("Pokkao Hub "," Premium Scripts ]")
local Tab1 = GUI:Tap("Genaral")
local Tab2 = GUI:Tap("Teleport")
local Tab3 = GUI:Tap("RTX GRAPHICS")
local Tab4 = GUI:Tap("others")
local Tab5 = GUI:Tap("Visuals")
local Tab6 = GUI:Tap("credits")
local Tab7 = GUI:Tap("CODE-REDEEM")
function TP2(P1)
    local Dis = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    local Speed
    if Dis < 1000 then
        Speed = 300
    elseif Dis >= 100 then
        Speed = 200
    end
    local tween = game:GetService("TweenService"):Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart,TweenInfo.new(Dis/Speed,Enum.EasingStyle.Linear),{CFrame = P1})
    tween:Play()
	_G.Part = true
end
Tab2:Line()
Tab2:Dropdown("Teleport in world 1",{"PirateDefault", "Jungle", "central island", "sand island", "Pirate Land", "iceland", "Prison", "Marine Land", "Colosseum", "LV.600+ LAND", "undersea city", "Marine Defauit"},function(t)
    _G.Teleport = t
end)

Tab2:Line()

Tab2:Button("Tween",function(value)
    pcall(function()
        if _G.Teleport == "PirateDefault" then
            TP2(CFrame.new(1020.9113159179688, 95.82339477539062, 1567.62890625))
        elseif _G.Teleport == "Jungle" then
             TP2(CFrame.new(-1605.92236, 36.8521347, 149.120728, 0.0171093047, 4.86186309e-08, -0.999853611, -9.45663103e-08, 1, 4.70075463e-08, 0.999853611, 9.37481985e-08, 0.0171093047))
         elseif _G.Teleport == "central island" then
             TP2(CFrame.new(-784.29248046875, 33.65190124511719, 1606.9835205078125))
         elseif
             _G.Teleport == "sand island" then
            TP2(CFrame.new(1330.142333984375, 101.86573791503906, 4489.53955078125)) 
             elseif
              _G.Teleport == "Pirate Land" then
            TP2(CFrame.new(-1252.4139404296875, 44.55205535888672, 3820.52392578125)) 
              elseif
              _G.Teleport == "iceland" then
            TP2(CFrame.new(1222.4112548828125, 70.81449127197266, -1243.112548828125)) 
              elseif
              _G.Teleport == "Prison" then
            TP2(CFrame.new(5010.4150390625, 88.6519775390625, 738.5647583007812)) 
              elseif
              _G.Teleport == "Marine Land" then
            TP2(CFrame.new(-5150.67724609375, 375.9053649902344, 4443.45654296875)) 
              elseif
              _G.Teleport == "Colosseum" then
            TP2(CFrame.new(-1829.173583984375, 80.37115478515625, -3054.580810546875)) 
              elseif
              _G.Teleport == "LV.600+ LAND" then
            TP2(CFrame.new(5052.1962890625, 48.429481506347656, 4057.39306640625)) 
              elseif
              _G.Teleport == "undersea city" then
            TP2(CFrame.new(4049.18798828125, 1.9886010885238647, -1815.5950927734375)) 
              elseif
              _G.Teleport == "comeback undersea city" then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))))
         elseif     _G.Teleport == "Marine Defauit" then
            TP2(CFrame.new(61169.515625, 1.6770490407943726, 1953.4300537109375)) 
         else
            StopTween(_G.Teleport)
         end
    end)
end)

Tab2:Button("Stop Tween",function(value)
    pcall(function()
        TP2(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
		_G.Part = false
    end)
end)




spawn(function()
    pcall(function()
       game:GetService("RunService").Heartbeat:Connect(function()
        if _G.Part then
          if not game:GetService("Workspace"):FindFirstChild("LOL") then
             local Paertaiteen = Instance.new("Part")
             Paertaiteen.Name = "LOL"
             Paertaiteen.Parent = game.Workspace
             Paertaiteen.Anchored = true
             Paertaiteen.Transparency = 1
             Paertaiteen.Size = Vector3.new(15,0.5,15)
             Paertaiteen.Material = "Neon"
             while true do 
                 wait(0.1) 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 155, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 155, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 155)}):Play() 
                 wait(.5)
             end 
         elseif game:GetService("Workspace"):FindFirstChild("LOL") then
             game.Workspace["LOL"].CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Y - 3.92,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
         end
     else
         if game:GetService("Workspace"):FindFirstChild("LOL") then
             game:GetService("Workspace"):FindFirstChild("LOL"):Destroy()
         end
        end
    end)
 end)
end)




local X2Code = {
    "TheGreatAce",        
    "Bignews",      
    "Fudd10",
    "Axiore",
    "TantaiGaming",
    "StrawHatMaine",
    "Sub20fficialNoobie",
    "Sub2NoobMaster123",
    "Sub2Daigrock",
    "SUB2GAMERROBOT_EXP1",
    "UPD16",
    "3BVISITS",
    "fudd10_v2",
    "Bluxxy",
    "JCWK",
    "Sub2Fer999",
    "Enyu_is_Pro",
    "Magicbus",
    "Starcodeheo"
}

Tab7:Button("RedeemAllCodex2",function(value)
    function RedeemCode(value)
        game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(value)
    end
    for i,v in pairs(x2Code) do
        RedeemCode(v)
    end
end)

Tab3:Line()
Tab3:Button("RTX ON",function(value)
    pcall(function()
     getgenv().mode = "Autumn" -- Choose from Summer and Autumn
            settings().Rendering.QualityLevel = 10
            local a = game.Lighting
            a.Ambient = Color3.fromRGB(33, 33, 33)
            a.Brightness = 6.67
            a.ColorShift_Bottom = Color3.fromRGB(0, 0, 0)
            a.ColorShift_Top = Color3.fromRGB(255, 247, 237)
            a.EnvironmentDiffuseScale = 0.105
            a.EnvironmentSpecularScale = 0.522
            a.GlobalShadows = true
            a.OutdoorAmbient = Color3.fromRGB(51, 54, 67)
            a.ShadowSoftness = 0.04
            a.GeographicLatitude = -15.525
            a.ExposureCompensation = 0.75
            local b = Instance.new("BloomEffect", a)
            b.Enabled = true
            b.Intensity = 0.04
            b.Size = 1900
            b.Threshold = 0.915
            local c = Instance.new("ColorCorrectionEffect", a)
            c.Brightness = 0.176
            c.Contrast = 0.39
            c.Enabled = true
            c.Saturation = 0.2
            c.TintColor = Color3.fromRGB(217, 145, 57)
            if getgenv().mode == "Summer" then
                c.TintColor = Color3.fromRGB(255, 220, 148)
            elseif getgenv().mode == "Autumn" then
                c.TintColor = Color3.fromRGB(217, 145, 57)
            else
                warn("No mode selected!")
                print("Please select a mode")
                b:Destroy()
                c:Destroy()
            end
            local d = Instance.new("DepthOfFieldEffect", a)
            d.Enabled = true
            d.FarIntensity = 0.077
            d.FocusDistance = 21.54
            d.InFocusRadius = 20.77
            d.NearIntensity = 0.277
            local e = Instance.new("ColorCorrectionEffect", a)
            e.Brightness = 0
            e.Contrast = -0.07
            e.Saturation = 0
            e.Enabled = true
            e.TintColor = Color3.fromRGB(255, 247, 239)
            local e2 = Instance.new("ColorCorrectionEffect", a)
            e2.Brightness = 0.2
            e2.Contrast = 0.45
            e2.Saturation = -0.1
            e2.Enabled = true
            e2.TintColor = Color3.fromRGB(255, 255, 255)
            local s = Instance.new("SunRaysEffect", a)
            s.Enabled = true
            s.Intensity = 0.01
            s.Spread = 0.146
    end)
end)

Tab3:Button("RTX OFF",function(value)
        pcall(function()
	local light = game.Lighting
	for i, v in pairs(light:GetChildren()) do
		v:Destroy()
	end

	local ter = workspace.Terrain
	local color = Instance.new("ColorCorrectionEffect")
	local bloom = Instance.new("BloomEffect")
	local sun = Instance.new("SunRaysEffect")
	local blur = Instance.new("BlurEffect")

	color.Parent = light
	bloom.Parent = light
	sun.Parent = light
	blur.Parent = light

	-- enable or disable shit

	local config = {

		Terrain = true;
		ColorCorrection = true;
		Sun = true;
		Lighting = true;
		BloomEffect = true;

	}

	-- settings {

	color.Enabled = false
	color.Contrast = 0.15
	color.Brightness = 0.1
	color.Saturation = 0.25
	color.TintColor = Color3.fromRGB(255, 222, 211)

	bloom.Enabled = false
	bloom.Intensity = 0.1

	sun.Enabled = false
	sun.Intensity = 0.2
	sun.Spread = 1

	bloom.Enabled = false
	bloom.Intensity = 0.05
	bloom.Size = 32
	bloom.Threshold = 1

	blur.Enabled = false
	blur.Size = 6

	-- settings }


	if config.ColorCorrection then
		color.Enabled = true
	end


	if config.Sun then
		sun.Enabled = true
	end


	if config.Terrain then
		-- settings {
		ter.WaterColor = Color3.fromRGB(10, 10, 24)
		ter.WaterWaveSize = 0.1
		ter.WaterWaveSpeed = 22
		ter.WaterTransparency = 0.9
		ter.WaterReflectance = 0.05
		-- settings }
	end


	if config.Lighting then
		-- settings {
		light.Ambient = Color3.fromRGB(0, 0, 0)
		light.Brightness = 4
		light.ColorShift_Bottom = Color3.fromRGB(0, 0, 0)
		light.ColorShift_Top = Color3.fromRGB(0, 0, 0)
		light.ExposureCompensation = 0
		light.FogColor = Color3.fromRGB(132, 132, 132)
		light.GlobalShadows = true
		light.OutdoorAmbient = Color3.fromRGB(112, 117, 128)
		light.Outlines = false
		else
	end
    end)
end)

Tab5:Line()
Tab5:Button("Teleport to First sea",function(value)
        pcall(function()
        end)
end)

Tab5:Line()
Tab5:Button("Teleport to Second sea",function(value)
        pcall(function()
        end)
end)

Tab5:Line()
Tab5:Button("Teleport to Third sea",function(value)
        pcall(function()
        end)
end)
Tab5:Line()
Tab4:Line()
Tab4:Button("Hand Fire FIVEM",function(value)
        pcall(function()
            local Fire = Instance.new("Fire")
Fire.Parent = game.Players.LocalPlayer.Character.RightHand
Fire.Heat = 5
Fire.Size = 2
        end)
end)
Tab4:Line()

Tab2:Line()
Tab3:Line()


Tab4:Button("Fake Mink V.4",function(value)
        pcall(function()
            game.Players.LocalPlayer.Character.Humanoid:LoadAnimation(game:GetService("ReplicatedStorage").Util.Anims.Storage[2].RaceTransform):Play()
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Player = game:GetService("Players").LocalPlayer

local ArgsDash = {
    Character = Player.Character,
    Duration = .25,
    CFrame = Player.Character.HumanoidRootPart.CFrame,
}

local old; old = hookmetamethod(game, "__namecall", newcclosure(function(self, ...)
    if self.Name == "CommE" then
        local args = {...}

        if args[1] == "Dodge" then
            coroutine.wrap(function() require(ReplicatedStorage.Effect.Container.Shared.LightningTP)(ArgsDash) end)()
        end
    end

    return old(self, ...)
end))

game.players.LocalPlayer.Character.Humanoid.WalkSpeed = 50
end)
end)
Tab4:Line()

Tab6:Line()
Tab6:Button(" credit Fake Mink V.4",function(value)
        pcall(function()
        end)
end)


Tab6:Button("👇",function(value)
        pcall(function()
        end)
end)


Tab6:Button("Beluga.#2332",function(value)
        pcall(function()
        end)
end)
Tab6:Line()


Tab6:Button("credit Hand Fire FIVEM",function(value)
        pcall(function()
        end)
        
end)


Tab6:Button("👇",function(value)
        pcall(function()
        end)
        
end)


Tab6:Button("Semens Kung#0578",function(value)
        pcall(function()
        end)
        
end)
Tab6:Line()


Tab6:Button("credit RTX",function(value)
        pcall(function()
        end)
        
end)


Tab6:Button("👇",function(value)
        pcall(function()
        end)
        
end)


Tab6:Button("!A Bitter#6617",function(value)
        pcall(function()
        end)
        
end)


Tab5:Line()


Tab5:Button("Rejoin",function(value)
        pcall(function()
            local ts = game:GetService("TeleportService")

local p = game:GetService("Players").LocalPlayer

 

ts:Teleport(game.PlaceId, p)
end)
end)


Tab5:Line()


Tab5:Button("",function(value)
        pcall(function()
            game.Players.LocalPlayer.Character.Humanoid:LoadAnimation(game:GetService("White Screen [ Booster FPS ]",false,function(value)
    _G.WhiteScreen = value
if _G.WhiteScreen  then
    game:GetService("RunService"):Set3dRenderingEnabled(false)
else
    game:GetService("RunService"):Set3dRenderingEnabled(true)
end
end))
end)
end)


-- [Anti AFK]

game:GetService("Players").LocalPlayer.Idled:connect(function()
	game:GetService("VirtualUser"):Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
	wait(1)
	game:GetService("VirtualUser"):Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)


function TP2(P1)
    local Dis = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    local Speed
    if Dis < 1000 then
        Speed = 300
    elseif Dis >= 100 then
        Speed = 200
    end
    local tween = game:GetService("TweenService"):Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart,TweenInfo.new(Dis/Speed,Enum.EasingStyle.Linear),{CFrame = P1})
    tween:Play()
	_G.Part = true
end

Tab2:Dropdown("Teleport in world 2",{"skull island", "semi-tropical island", "semi-cold island", "Ice land", "Start Default world 2", "Cafe", "GreenBeach", "grave", "next to the grave", "haunted ship", "Boost Race V.2", "Boost Race V.3", "Colosseum"},function(t)
    _G.Teleport = t
end)

Tab2:Line()

Tab2:Button("Tween",function(value)
    pcall(function()
        if _G.Teleport == "skull island" then
            TP2(CFrame.new(-3224.809326171875, 473.8572998046875, -10244.6123046875))
        elseif _G.Teleport == "semi-tropical island" then
             TP2(CFrame.new(-5117.4365234375, 188.7383270263672, -5337.58740234375))
         elseif _G.Teleport == "semi-cold island" then
             TP2(CFrame.new(-6445.72900390625, 742.632568359375, -4959.9267578125))
         elseif
             _G.Teleport == "Ice land" then
            TP2(CFrame.new(656.2200317382812, 434.3799743652344, -5345.23681640625)) 
             elseif
              _G.Teleport == "Start Default world 2" then
            TP2(CFrame.new(-33.22943115234375, 39.16966247558594, 2654.123046875)) 
              elseif
              _G.Teleport == "Cafe" then
            TP2(CFrame.new(-387.60211181640625, 136.32057189941406, 369.9222717285156)) 
              elseif
              _G.Teleport == "GreenBeach" then
            TP2(CFrame.new(-2410.935791015625, 226.19805908203125, -3641.08984375)) 
              elseif
              _G.Teleport == "grave" then
            TP2(CFrame.new(-5651.32568359375, 266.49383544921875, -760.3703002929688)) 
              elseif
              _G.Teleport == "next to the grave" then
            TP2(CFrame.new(-6014.4013671875, 6.428503036499023, -1351.05029296875)) 
              elseif
              _G.Teleport == "haunted ship" then
            TP2(CFrame.new(-6560.22509765625, 552.0887451171875, -207.6063232421875)) 
              elseif
              _G.Teleport == "Boost Race V.2" then
            TP2(CFrame.new(-2773.942138671875, 72.9919204711914, -3567.228515625)) 
              elseif
                    _G.Teleport == "Boost Race V.3" then
            TP2(CFrame.new(-1976.065185546875, 129.33921813964844, -68.54853820800781)) 
              elseif
              _G.Teleport == "" then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))))
         elseif     _G.Teleport == "Colosseum" then
            TP2(CFrame.new(-1940.0858154296875, 241.65411376953125, 1750.079833984375)) 
         else
            StopTween(_G.Teleport)
         end
    end)
end)



Tab2:Button("Stop Tween",function(value)
    pcall(function()
        TP2(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
		_G.Part = false
    end)
end)




spawn(function()
    pcall(function()
       game:GetService("RunService").Heartbeat:Connect(function()
        if _G.Part then
          if not game:GetService("Workspace"):FindFirstChild("LOL") then
             local Paertaiteen = Instance.new("Part")
             Paertaiteen.Name = "LOL"
             Paertaiteen.Parent = game.Workspace
             Paertaiteen.Anchored = true
             Paertaiteen.Transparency = 1
             Paertaiteen.Size = Vector3.new(15,0.5,15)
             Paertaiteen.Material = "Neon"
             while true do 
                 wait(0.1) 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 155, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 155, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 155)}):Play() 
                 wait(.5)
             end 
         elseif game:GetService("Workspace"):FindFirstChild("LOL") then
             game.Workspace["LOL"].CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Y - 3.92,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
         end
     else
         if game:GetService("Workspace"):FindFirstChild("LOL") then
             game:GetService("Workspace"):FindFirstChild("LOL"):Destroy()
         end
        end
    end)
 end)
end)


Tab1:Toggle("AuToFarm",function(value)
    _G.AutoFarmza = value
end)


spawn(function()
    while wait() do 
        pcall(function()
            if _G.AutoFarmza then
                if QuestVis() then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text:find(NameMon) then
                        if game:GetService("Workspace").Enemies:FindFirstChild(Mon) then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == Mon then
                                    v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    v.HumanoidRootPart.CanCollide = false
                                    EquipTool(_G.Weapon)
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,30,0)
                                    game:GetService("VirtualUser"):CaptureController()
                                    game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                end
                            end
                        else
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = PosPuk
                        end
                    else    
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(AbandonQuest)
                    end
                elseif not QuestVis() then
                    TP2(PosQ)
                    if (PosQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
                        wait(1.5)
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",QuestName,QuestNumber)
                    end
                end
            end
        end)
    end
end)


Tab1:Toggle("BringMon",function(value)
    _G.BringMon = value
end)


spawn(function()
    while task.wait() do
        pcall(function()
            if _G.BringMon then  
                CheckLevel()
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    for x,y in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if y.Name == Mon and v.Name == Mon then
                            v.HumanoidRootPart.CFrame = y.HumanoidRootPart.CFrame
                            v.HumanoidRootPart.CanCollide = false
                            y.HumanoidRootPart.CanCollide = false
                            v.Humanoid.WalkSpeed = nil
                            y.Humanoid.WalkSpeed = nil
                            v.Humanoid:ChangeState(2)
                            y.Humanoid:ChangeState(2)
                            v.Humanoid.JumpPower = 0
                            y.Humanoid.JumpPower = 0
                             if sethiddenproperty then
                                sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                                
                            end
                        end
                    end
                end
            end
        end)
    end
end)
