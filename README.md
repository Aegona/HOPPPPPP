

local CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
local Camera = require(game.ReplicatedStorage.Util.CameraShaker)
Camera:Stop()
coroutine.wrap(function()
    game:GetService("RunService").Stepped:Connect(function()
        if getupvalues(CombatFramework)[2]['activeController'].timeToNextAttack then
            getupvalues(CombatFramework)[2]['activeController'].timeToNextAttack = 0
            getupvalues(CombatFramework)[2]['activeController'].hitboxMagnitude = 50
            getupvalues(CombatFramework)[2]['activeController']:attack()
        end
    end)
end)()




function CheckQuest()
   local Lv =  game.Players.LocalPlayer.Data.Level.Value
   if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
   elseif  Lv == 1 or Lv <= 9 then
       Ms = "Bandit [Lv. 5]"
       CQ = CFrame.new(1059.838623046875, 16.516624450683594, 1545.941162109375)
       CM = CFrame.new(1177.2108154296875, 16.43285369873047, 1616.587646484375)
       NQ = "BanditQuest1"
       NM = "Bandit"
       LQ = 1
   elseif Lv == 10 or Lv <= 14 then
      Ms = "Monkey [Lv. 14]"
       CQ = CFrame.new(-1602.7935791015625, 36.977455139160156, 152.5421905517578)
       CM = CFrame.new(-1447.2706298828125, 22.977434158325195, 164.9077911376953)
       NQ = "JungleQuest"
       NM = "Monkey"
       LQ = 1
          elseif Lv == 15 or Lv <= 2999 then
      Ms = "Gorilla [Lv. 20]"
       CQ = CFrame.new(-1602.7935791015625, 36.977455139160156, 152.5421905517578)
       CM = CFrame.new(-1221.9395751953125, 6.404693126678467, -500.5191955566406)
       NQ = "JungleQuest"
       NM = "Gorilla"
       LQ = 2
   end
end

local GUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/Patskorn/GUI/main/Daino.lua"))()
local idk = GUI:new()
local win = idk:Tap("Farm")

win:Toggle("Auto Farm",true,function(value)
_G.Farm = value
_G.BringMob = value
end)



function TP(P)
    NoClip = true
    Distance = (P.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    if Distance < 10 then
        Speed = 1000
    elseif Distance < 170 then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = P
        Speed = 350
    elseif Distance < 1000 then
        Speed = 350
    elseif Distance >= 1000 then
        Speed = 280
    end
    game:GetService("TweenService"):Create(
        game.Players.LocalPlayer.Character.HumanoidRootPart,
        TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
        {CFrame = P}
    ):Play()
    NoClip = false
end

spawn(function()
    while wait() do
        if _G.Farm then
            CheckQuest()
            if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                
                TP(CQ)
                
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NQ,LQ)
                
            elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v.Name == Ms then
                        CM = v.HumanoidRootPart.CFrame
                        CM = v.HumanoidRootPart.CFrame
                        CM = v.HumanoidRootPart.CFrame
                        CM = v.HumanoidRootPart.CFrame
                        CM = v.HumanoidRootPart.CFrame
                        TP(v.HumanoidRootPart.CFrame * CFrame.new(0,25,0))
                        end
                    end
                end
            end    
        end
    end)

spawn(function()
    pcall(function()
        while task.wait() do
            if _G.Farm then
                if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                    local Noclip = Instance.new("BodyVelocity")
                    Noclip.Name = "BodyClip"
                    Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
                    Noclip.MaxForce = Vector3.new(100000,100000,100000)
                    Noclip.Velocity = Vector3.new(0,0,0)
                end
            else
                if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                    game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
                end
            end
        end
    end)
end)



spawn(function()
    while task.wait() do
        if _G.Farm then
        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
            if v.Name == Ms then
                v.HumanoidRootPart.CFrame = CM
                                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CFrame = CM
                v.HumanoidRootPart.CanCollide = false
                sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                end
            end
        end
    end
end)


             while _G.BringMob do wait()
            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                 for i2,v2 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v.Name == MON and v2.Name == MON then
                        v2.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                        v2.HumanoidRootPart.CanCollide = false
                           game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * Method
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                    end
                 end
            end
             end
             
             Time = 1 -- seconds
repeat wait() until game:IsLoaded()
wait(Time)
local PlaceID = game.PlaceId
local AllIDs = {}
local foundAnything = ""
local actualHour = os.date("!*t").hour
local Deleted = false
function TPReturner()
   local Site;
   if foundAnything == "" then
       Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
   else
       Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
   end
   local ID = "2753915549"
   if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
       foundAnything = Site.nextPageCursor
   end
   local num = 0;
   for i,v in pairs(Site.data) do
       local Possible = true
       ID = tostring(v.id)
       if tonumber(v.maxPlayers) > tonumber(v.playing) then
           for _,Existing in pairs(AllIDs) do
               if num ~= 0 then
                   if ID == tostring(Existing) then
                       Possible = false
                   end
               else
                   if tonumber(actualHour) ~= tonumber(Existing) then
                       local delFile = pcall(function()
                           delfile("NotSameServers.json")
                           AllIDs = {}
                           table.insert(AllIDs, actualHour)
                       end)
                   end
               end
               num = num + 1
           end
           if Possible == true then
               table.insert(AllIDs, ID)
               wait()
               pcall(function()
                   writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
                   wait()
                   game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
               end)
               wait(4)
           end
       end
   end
end
 
function Teleport()
   while wait() do
       pcall(function()
           TPReturner()
           if foundAnything ~= "" then
               TPReturner()
           end
       end)
   end
end
 function Banhop1()
   for i,v in pairs(game:GetService("Players"):GetDescendants()) do
       if v.Name == HopPlayer1 then
           wait(2)
           Teleport()
           end
       end
 end
 
  function Banhop2()
   for i,v in pairs(game:GetService("Players"):GetDescendants()) do
       if v.Name == HopPlayer2 then
           wait(2)
           Teleport()
           end
       end
  end
 function Banhop3()
   for i,v in pairs(game:GetService("Players"):GetDescendants()) do
       if v.Name == HopPlayer3 then
           wait(2)
           Teleport()
           end
       end
 end
  function Banhop4()
   for i,v in pairs(game:GetService("Players"):GetDescendants()) do
       if v.Name == HopPlayer4 then
           wait(2)
           Teleport()
           end
       end
 end
Banhop1()
Banhop2()
Banhop3()
Banhop4()
