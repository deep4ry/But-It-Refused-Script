# But-It-Refused-Script
but it refused

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local isActive = false
local deathPosition = nil

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game:GetService("CoreGui")

local dragFrame = Instance.new("Frame")
dragFrame.Size = UDim2.new(0, 220, 0, 150)
dragFrame.Position = UDim2.new(0, 10, 0, 10)
dragFrame.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
dragFrame.BackgroundTransparency = 0.3
dragFrame.Active = true
dragFrame.Draggable = true
dragFrame.Parent = screenGui

local toggleButton = Instance.new("TextButton")
toggleButton.Size = UDim2.new(0, 200, 0, 50)
toggleButton.Position = UDim2.new(0, 10, 0, 50)
toggleButton.Text = "But It Refused: OFF"
toggleButton.BackgroundColor3 = Color3.new(0.8, 0.8, 0.8)
toggleButton.TextColor3 = Color3.new(0, 0, 0)
toggleButton.Parent = dragFrame

toggleButton.MouseButton1Click:Connect(function()
    isActive = not isActive
    toggleButton.Text = isActive and "But It Refused: ON" or "But It Refused: OFF"
end)

local function onDeath()
    if isActive and character and character.PrimaryPart then
        deathPosition = character.PrimaryPart.Position
    else
        deathPosition = nil
    end
end

local function onRespawn(newCharacter)
    character = newCharacter
    if isActive and deathPosition then
        character:WaitForChild("HumanoidRootPart").CFrame = CFrame.new(deathPosition)
    end
end

player.CharacterRemoving:Connect(onDeath)
player.CharacterAdded:Connect(onRespawn)
