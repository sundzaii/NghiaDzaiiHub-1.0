local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.CoreGui

local Frame = Instance.new("Frame")
Frame.Parent = ScreenGui
Frame.Size = UDim2.new(0,220,0,140)
Frame.Position = UDim2.new(0.5,-110,0.5,-70)
Frame.BackgroundColor3 = Color3.fromRGB(35,35,35)

local Title = Instance.new("TextLabel")
Title.Parent = Frame
Title.Size = UDim2.new(1,0,0,25)
Title.BackgroundTransparency = 1
Title.Text = "nghiadzai"
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.TextScaled = true

local TextBox = Instance.new("TextBox")
TextBox.Parent = Frame
TextBox.Size = UDim2.new(0,180,0,35)
TextBox.Position = UDim2.new(0.5,-90,0,35)
TextBox.PlaceholderText = "Speed 1-100"
TextBox.Text = ""

local ApplyButton = Instance.new("TextButton")
ApplyButton.Parent = Frame
ApplyButton.Size = UDim2.new(0,180,0,35)
ApplyButton.Position = UDim2.new(0.5,-90,0,80)
ApplyButton.Text = "Apply"

local ToggleButton = Instance.new("TextButton")
ToggleButton.Parent = ScreenGui
ToggleButton.Size = UDim2.new(0,60,0,30)
ToggleButton.Position = UDim2.new(0,10,0.5,0)
ToggleButton.Text = "UI"
ToggleButton.Visible = false

-- Toggle (thu gọn xịn)
local opened = true

Frame:FindFirstChildWhichIsA("TextButton", true)

local function toggleUI()
    opened = not opened
    Frame.Visible = opened
    ToggleButton.Visible = not opened
end

Frame:FindFirstChildOfClass("TextButton")

-- X button
local X = Instance.new("TextButton")
X.Parent = Frame
X.Size = UDim2.new(0,25,0,25)
X.Position = UDim2.new(1,-25,0,0)
X.Text = "X"

X.MouseButton1Click:Connect(toggleUI)
ToggleButton.MouseButton1Click:Connect(toggleUI)

-- Speed
ApplyButton.MouseButton1Click:Connect(function()
    local speed = tonumber(TextBox.Text)
    if speed and speed >= 1 and speed <= 100 then
        local char = player.Character or player.CharacterAdded:Wait()
        char:WaitForChild("Humanoid").WalkSpeed = speed
    end
end)
