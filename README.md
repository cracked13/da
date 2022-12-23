local OwnerUsers = {
	["darckgames0103"] = true;
}

local WhitelistUsers = {
    ["GAB_LEALZINHO"] = true,
	["LICON777"] = true,
	["666X66666666X666"] = true,
    ["Omarlol9272"] = true,
    ["Doctor_Andreuian"] = true,
    ["Vinicius_2723"] = true,
}

if OwnerUsers[game.Players.LocalPlayer.Name] or WhitelistUsers[game.Players.LocalPlayer.Name] then
if game.Players.LocalPlayer.PlayerGui:FindFirstChild("ControlGui") then
    game.Players.LocalPlayer.PlayerGui:FindFirstChild("ControlGui"):Destroy()
end

game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("SpamArrest V5 GUI Loaded! | Made by 15yWhalixz2H", "All")
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("Good Luck For Who is Target This. -15yWhalixz2H", "All")

local function gplr(String)
	local Found = {}
	local strl = String:lower()
	if strl == "all" then
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			table.insert(Found,v)
		end
	elseif strl == "others" then
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			if v.Name ~= game.Players.LocalPlayer.Name then
				table.insert(Found,v)
			end
		end 
	elseif strl == "me" then
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			if v.Name == game.Players.LocalPlayer.Name then
				table.insert(Found,v)
			end
		end 
	else
		for i,v in pairs(game:GetService("Players"):GetPlayers()) do
			if v.DisplayName:lower():sub(1, #String) == String:lower() or v.Name:lower():sub(1, #String) == String:lower() then
				table.insert(Found,v)
			end
		end 
	end
	return Found 
end

game:GetService("RunService").RenderStepped:Connect(function()
for i,v in pairs(game:GetService("Players"):GetChildren()) do
if v.Character then
for i2,v2 in pairs(v.Character:GetDescendants()) do
if v2.Name == "handcuffedGui" then
v2:Destroy()
end    
end
end
end
game:GetService("Workspace").Remote.TeamEvent:FireServer("Bright orange")
end)

-- Objects
plr = game.Players.LocalPlayer
ControlGui = Instance.new("ScreenGui")
Frame = Instance.new("Frame")
TextLabel = Instance.new("TextLabel")
TextButton = Instance.new("TextButton")
TextBox = Instance.new("TextBox")

-- Properties

ControlGui.Name = "CrashGui"
ControlGui.Parent = plr.PlayerGui
ControlGui.ResetOnSpawn = false

Frame.Parent = ControlGui
Frame.BackgroundColor3 = Color3.new(1, 1, 1)
Frame.Position = UDim2.new(0, 300, 0, 200)
Frame.Size = UDim2.new(0, 300, 0, 200)
Frame.Active = true
Frame.Draggable = true

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.new(1, 1, 1)
TextLabel.BackgroundTransparency = 5
TextLabel.Size = UDim2.new(0, 200, 0, 50)
TextLabel.Position = UDim2.new(0, 50, 0, 10)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.FontSize = Enum.FontSize.Size32
TextLabel.Text = "Script Made by: Whalix();#0265"
TextLabel.TextScaled = true
TextLabel.TextSize = 20
TextLabel.TextWrapped = true

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.new(1, 1, 1)
TextButton.Position = UDim2.new(0, 50, 0, 120)
TextButton.Size = UDim2.new(0, 200, 0, 50)
TextButton.Font = Enum.Font.SourceSans
TextButton.FontSize = Enum.FontSize.Size32
TextButton.Text = "SpamArrest V5"
TextButton.TextSize = 15
TextButton.MouseButton1Down:connect(function()
local Player = gplr(TextBox.Text)
if Player[1] then
Player = Player[1]

function GetCorrectRootPartCFrame()
if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart then
local x, y, z = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame:ToOrientation()
return CFrame.new(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.X, game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y, game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Z) * CFrame.fromOrientation(x, y, z)
end
end

function GetCorrectCameraCFrame()
if game:GetService("Workspace").Camera then
local x, y, z = game:GetService("Workspace").Camera.CFrame:ToOrientation()
return CFrame.new(game:GetService("Workspace").Camera.CFrame.X, game:GetService("Workspace").Camera.CFrame.Y, game:GetService("Workspace").Camera.CFrame.Z) * CFrame.fromOrientation(x, y, z)
end
end

local HumanoidRootPartLastCFrame = GetCorrectRootPartCFrame()
local CameraLastCFrame = GetCorrectCameraCFrame()

function SaveCFrame()
CameraLastCFrame = GetCorrectCameraCFrame()
HumanoidRootPartLastCFrame = GetCorrectRootPartCFrame()
end

function LoadCFrame()
for i = 1, 2 do
game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = HumanoidRootPartLastCFrame
game:GetService("Workspace").Camera.CFrame = CameraLastCFrame
end
end

function LoadCharacter(Color)
local Color = Color or nil
game:GetService("Workspace").Remote.loadchar:InvokeServer(nil, Color)
end

function FeGod()
if game:GetService("Players").LocalPlayer.Character.Humanoid then
local New = game:GetService("Players").LocalPlayer.Character.Humanoid:Clone()
New.Parent = game:GetService("Players").LocalPlayer.Character
New.Name = "Humanoid"
game:GetService("Players").LocalPlayer.Character.Humanoid:Destroy()
game:GetService("Workspace").Camera.CameraSubject = game:GetService("Players").LocalPlayer.Character
local Animate = game:GetService("Players").LocalPlayer.Character:FindFirstChild("Animate") or game:GetService("Players").LocalPlayer.Character:WaitForChild("Animate")
if Animate then
Animate.Disabled = true
wait()
Animate.Disabled = false
end
New.DisplayDistanceType = "None"
end
end


connection = game:GetService("RunService").RenderStepped:Connect(function()
for i = 0, 10, 10 do
coroutine.wrap(function()
for i = 0, 5, 5 do
if game:GetService("Players").LocalPlayer and game:GetService("Players").LocalPlayer.Character and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Torso") and Player and Player.Character and Player.Character:FindFirstChild("Torso") then
game:GetService("Workspace").Remote.arrest:InvokeServer(Player.Character.Torso)
end
end
end)()
end
end)

repeat
pcall(function()
if Player.TeamColor.Name ~= "Really red" then
local SpawnCriminal = game.Workspace["Criminals Spawn"].SpawnLocation
local OldCFrameSpawnCriminal = SpawnCriminal.CFrame
local OldCanCollideSpawnCriminal = SpawnCriminal.CanCollide
local OldAnchoredSpawnCriminal = SpawnCriminal.Anchored
local OldTransparencySpawnCriminal = SpawnCriminal.Transparency
SpawnCriminal.CanCollide = false
SpawnCriminal.Anchored = true
SpawnCriminal.Transparency = 5
SaveCFrame()
LoadCharacter()
wait(0.1)
LoadCFrame()
FeGod()
if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hammer") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hammer") then
game:GetService("Workspace").Remote.ItemHandler:InvokeServer(game:GetService("Workspace").Prison_ITEMS.single:FindFirstChild("Hammer").ITEMPICKUP)
end
wait(0.1)
local Tool = game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hammer")
Tool.Parent = game.Players.LocalPlayer.Character
local stop = 0
repeat
pcall(function()
stop = stop + 1
if game:GetService("Players").LocalPlayer.Character.Humanoid.Sit == true then
game:GetService("Players").LocalPlayer.Character.Humanoid.Sit = false
end
if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart and Player.Character.HumanoidRootPart then
Player.Character.HumanoidRootPart.CFrame = Tool.Handle.CFrame
SpawnCriminal.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
end
end)
game:GetService("RunService").RenderStepped:Wait()
until not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hammer") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Parent or not Player.Character:FindFirstChild("HumanoidRootPart") or not Player.Character:FindFirstChild("HumanoidRootPart").Parent or not game.Players:FindFirstChild(Player.Name) or stop > 50
wait()
SpawnCriminal.CFrame = OldCFrameSpawnCriminal
SpawnCriminal.CanCollide = OldCanCollideSpawnCriminal
SpawnCriminal.Anchored = OldAnchoredSpawnCriminal
SpawnCriminal.Transparency = OldTransparencySpawnCriminal
LoadCharacter()
wait(0.1)
LoadCFrame()
wait(0.2)
else
local temp = 0
repeat
pcall(function()
temp = temp + 1
if game:GetService("Players").LocalPlayer.Character.Humanoid.Sit == true then
game:GetService("Players").LocalPlayer.Character.Humanoid.Sit = false
end
if game:GetService("Players").LocalPlayer and game:GetService("Players").LocalPlayer.Character and game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") and Player and Player.Character and Player.Character:FindFirstChild("HumanoidRootPart") then
game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = Player.Character.HumanoidRootPart.CFrame
end
end)
game:GetService("RunService").RenderStepped:Wait()
until not game:GetService("Players").LocalPlayer.Character.Head or not Player.Character.Head or Player.Character.Head:FindFirstChild("handcuffedGui") or temp > 100
LoadCFrame()
end
end)
game:GetService("RunService").Stepped:Wait()
until not game.Players:FindFirstChild(Player.Name)
connection:Disconnect()
end
end)

TextBox.Parent = Frame
TextBox.BackgroundColor3 = Color3.new(1, 1, 1)
TextBox.Position = UDim2.new(0, 50, 0, 70)
TextBox.Size = UDim2.new(0, 200, 0, 30)
TextBox.Font = Enum.Font.SourceSans
TextBox.FontSize = Enum.FontSize.Size28
TextBox.Text = "Target"
TextBox.TextSize = 25

spawn(function()
while wait() do
pcall(function()
if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position.Y < 1 then
game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(769, 396, 2675)
wait()
SaveCFrame()
end
end)
end
end)

spawn(function()
while wait() do
pcall(function()
if game:GetService("Players").LocalPlayer.Character.Humanoid.Health < 50 then
SaveCFrame()
LoadCharacter()
wait(0.1)
LoadCFrame()
end
end)
end
end)
else
game.Players.LocalPlayer:Kick("Not Whitelisted.")
end
