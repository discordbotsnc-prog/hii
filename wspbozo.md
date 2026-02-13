local authorizedUserId = 4124578818 -- Your User ID
local player = game.Players.LocalPlayer
local gui = player:WaitForChild("PlayerGui")

-- Key prompt UI
local keyPrompt = Instance.new("ScreenGui")
keyPrompt.Name = "KeyPrompt"
keyPrompt.Parent = gui

local promptFrame = Instance.new("Frame")
promptFrame.Size = UDim2.new(0, 350, 0, 150)
promptFrame.Position = UDim2.new(0.5, -175, 0.5, -75)
promptFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
promptFrame.BorderSizePixel = 2
promptFrame.Parent = keyPrompt

local label = Instance.new("TextLabel")
label.Size = UDim2.new(1, 0, 0, 30)
label.Position = UDim2.new(0, 0, 0, 0)
label.Text = "Enter the key: KEY IS  1234"
label.TextColor3 = Color3.new(1, 1, 1)
label.BackgroundTransparency = 1
label.Font = Enum.Font.SourceSansBold
label.TextSize = 20
label.Parent = promptFrame

local keyInput = Instance.new("TextBox")
keyInput.Size = UDim2.new(1, -20, 0, 35)
keyInput.Position = UDim2.new(0, 10, 0, 50)
keyInput.PlaceholderText = "Your key here"
keyInput.Text = ""
keyInput.TextColor3 = Color3.new(1, 1, 1)
keyInput.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
keyInput.ClearTextOnFocus = false
keyInput.Font = Enum.Font.SourceSans
keyInput.TextSize = 18
keyInput.Parent = promptFrame

local submitButton = Instance.new("TextButton")
submitButton.Size = UDim2.new(1, -20, 0, 35)
submitButton.Position = UDim2.new(0, 10, 0, 95)
submitButton.Text = "Submit"
submitButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
submitButton.TextColor3 = Color3.new(1, 1, 1)
submitButton.Font = Enum.Font.SourceSansBold
submitButton.TextSize = 20
submitButton.Parent = promptFrame

-- Main UI creation function focused on ScriptHub with search bar
local function createUI()
    -- Authorization check
    if player.UserId ~= authorizedUserId then
        player:Kick("You are not authorized to run this script.")
        return
    end

    -- Remove existing UI if any
    local existingUI = player.PlayerGui:FindFirstChild("699 Hub")
    if existingUI then existingUI:Destroy() end

    local executorUI = Instance.new("ScreenGui")
    executorUI.Name = "699 Hub"
    executorUI.Parent = player.PlayerGui

    local mainFrame = Instance.new("Frame")
    mainFrame.Size = UDim2.new(0, 500, 0, 400)
    mainFrame.Position = UDim2.new(0.5, -250, 0.5, -200)
    mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    mainFrame.BorderSizePixel = 2
    mainFrame.Parent = executorUI

    -- Draggable main frame
    local dragging = false
    local dragInput
    local dragStart
    local startPos

    mainFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            dragStart = input.Position
            startPos = mainFrame.Position

            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    mainFrame.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            dragInput = input
        end
    end)

    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            local delta = input.Position - dragStart
            mainFrame.Position = UDim2.new(
                startPos.X.Scale,
                startPos.X.Offset + delta.X,
                startPos.Y.Scale,
                startPos.Y.Offset + delta.Y
            )
        end
    end)

    -- Title label
    local titleLabel = Instance.new("TextLabel")
    titleLabel.Size = UDim2.new(1, 0, 0, 40)
    titleLabel.Position = UDim2.new(0, 0, 0, 0)
    titleLabel.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
    titleLabel.Text = "699 Hub - ScriptHub"
    titleLabel.TextColor3 = Color3.new(1, 1, 1)
    titleLabel.Font = Enum.Font.SourceSansBold
    titleLabel.TextSize = 24
    titleLabel.Parent = mainFrame

    -- Search box
    local searchBox = Instance.new("TextBox")
    searchBox.Size = UDim2.new(1, -20, 0, 30)
    searchBox.Position = UDim2.new(0, 10, 0, 50)
    searchBox.PlaceholderText = "Search scripts..."
    searchBox.Text = ""
    searchBox.TextColor3 = Color3.new(1, 1, 1)
    searchBox.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    searchBox.Font = Enum.Font.SourceSans
    searchBox.TextSize = 20
    searchBox.Parent = mainFrame

    -- Scrolling frame for scripts
    local scriptList = Instance.new("ScrollingFrame")
    scriptList.Size = UDim2.new(1, -20, 1, -100)
    scriptList.Position = UDim2.new(0, 10, 0, 90)
    scriptList.CanvasSize = UDim2.new(0, 0, 0, 0)
    scriptList.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    scriptList.BorderSizePixel = 0
    scriptList.ScrollBarThickness = 6
    scriptList.Parent = mainFrame

    local uiListLayout = Instance.new("UIListLayout")
    uiListLayout.SortOrder = Enum.SortOrder.LayoutOrder
    uiListLayout.Padding = UDim.new(0, 5)
    uiListLayout.Parent = scriptList

    -- Table of scripts: name and function callback
    local scripts = {
        ["Escape Tsunami For Brainrots"] = function()
          local Players = game:GetService("Players")
local player = Players.LocalPlayer

local function createUI()
    -- Remove existing UI if any
    local existingUI = player.PlayerGui:FindFirstChild("699 Hub")
    if existingUI then
        existingUI:Destroy()
    end

    -- Show "Checking if allowed..."
    local messageLabel = Instance.new("TextLabel")
    messageLabel.Size = UDim2.new(0, 200, 0, 50)
    messageLabel.Position = UDim2.new(0.5, -100, 0.5, -25)
    messageLabel.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
    messageLabel.TextColor3 = Color3.new(1, 1, 1)
    messageLabel.Text = "Checking if allowed..."
    messageLabel.Parent = player.PlayerGui

    wait(1)

    local function isAuthorized()
        return player.UserId == authorizedUserId
    end

    if not isAuthorized() then
        messageLabel.Text = "Not allowed!"
        wait(2)
        player:Kick("You are not authorized to run this script.")
        return
    end

    messageLabel:Destroy()

    -- Create main UI
    local executorUI = Instance.new("ScreenGui")
    executorUI.Name = "699 Hub"
    executorUI.Parent = player.PlayerGui

    local mainFrame = Instance.new("Frame")
    mainFrame.Size = UDim2.new(0, 500, 0, 400)
    mainFrame.Position = UDim2.new(0.5, -250, 0.5, -200)
    mainFrame.BackgroundColor3 = Color3.fromRGB(30,30,30)
    mainFrame.BorderSizePixel = 2
    mainFrame.Parent = executorUI

    -- Draggable main frame
    local dragging = false
    local dragInput, dragStart, startPos

    mainFrame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            dragStart = input.Position
            startPos = mainFrame.Position
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    mainFrame.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            dragInput = input
        end
    end)

    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            local delta = input.Position - dragStart
            mainFrame.Position = startPos + UDim2.new(0, delta.X, 0, delta.Y)
        end
    end)

    -- Toggle button
    local toggleButton = Instance.new("TextButton")
    toggleButton.Size = UDim2.new(0, 100, 0, 30)
    toggleButton.Position = UDim2.new(0.5, -50, 0, -40)
    toggleButton.AnchorPoint = Vector2.new(0.5, 0)
    toggleButton.Text = "Open"
    toggleButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    toggleButton.TextColor3 = Color3.new(1, 1, 1)
    toggleButton.Parent = player.PlayerGui

    local uiVisible = true
    toggleButton.MouseButton1Click:Connect(function()
        uiVisible = not uiVisible
        mainFrame.Visible = uiVisible
        toggleButton.Text = uiVisible and "Close" or "Open"
    end)

    local categories = {"Main", "Fun", "Misc"}
    local buttons = {}
    local containers = {}

    local function createCategoryButton(name, yPos)
        local btn = Instance.new("TextButton")
        btn.Size = UDim2.new(0, 150, 0, 30)
        btn.Position = UDim2.new(0, 10, 0, yPos)
        btn.Text = name
        btn.BackgroundColor3 = Color3.fromRGB(50,50,50)
        btn.TextColor3 = Color3.new(1,1,1)
        btn.Parent = mainFrame
        return btn
    end

    for i, cat in ipairs(categories) do
        buttons[cat] = createCategoryButton(cat, (i-1)*40+10)
    end

    local function createContainer(yOffset)
        local container = Instance.new("Frame")
        container.Size = UDim2.new(1, -170, 1, -50)
        container.Position = UDim2.new(0, 160, 0, 50)
        container.BackgroundTransparency = 1
        container.Visible = false
        container.Parent = mainFrame
        return container
    end

    containers["Main"] = createContainer()
    containers["Fun"] = createContainer()
    containers["Misc"] = createContainer()

    local function showCategory(cat)
        for c, cont in pairs(containers) do
            cont.Visible = (c == cat)
        end
    end

    -- Button events
    for cat, btn in pairs(buttons) do
        btn.MouseButton1Click:Connect(function()
            showCategory(cat)
        end)
    end

    showCategory("Main") -- default

    -- ==========================
    -- MAIN: Remove VIPWalls inside DefaultMap_SharedInstances
    -- ==========================
    local vipObjectName = "VIPWalls"
    local removeVIPWallsBtn = Instance.new("TextButton")
    removeVIPWallsBtn.Size = UDim2.new(0, 200, 0, 40)
    removeVIPWallsBtn.Position = UDim2.new(0, 10, 0, 10)
    removeVIPWallsBtn.Text = "Remove VIP Walls"
    removeVIPWallsBtn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    removeVIPWallsBtn.TextColor3 = Color3.new(1, 1, 1)
    removeVIPWallsBtn.Parent = containers["Main"]

    removeVIPWallsBtn.MouseButton1Click:Connect(function()
        local vipFolder = workspace:FindFirstChild("DefaultMap_SharedInstances")
        if vipFolder then
            local vipWalls = vipFolder:FindFirstChild(vipObjectName)
            if vipWalls then
                vipWalls:Destroy()
                print("VIP Walls removed.")
            else
                print(vipObjectName .. " not found inside DefaultMap_SharedInstances.")
            end
        else
            print("DefaultMap_SharedInstances folder not found.")
        end
    end)

    -- ==========================
    -- FUN: Speed & Jump Power
    -- ==========================
    local function createInputButtonPair(container, labelText, defaultValue, callback)
        local label = Instance.new("TextLabel")
        label.Size = UDim2.new(0, 100, 0, 20)
        label.Position = UDim2.new(0, 10, 0, 10)
        label.Text = labelText
        label.TextColor3 = Color3.new(1,1,1)
        label.BackgroundTransparency = 1
        label.Parent = container

        local input = Instance.new("TextBox")
        input.Size = UDim2.new(0, 80, 0, 20)
        input.Position = UDim2.new(0, 120, 0, 10)
        input.Text = defaultValue
        input.Parent = container

        local button = Instance.new("TextButton")
        button.Size = UDim2.new(0, 80, 0, 20)
        button.Position = UDim2.new(0, 210, 0, 10)
        button.Text = "Set"
        button.BackgroundColor3 = Color3.fromRGB(70,70,70)
        button.TextColor3 = Color3.new(1,1,1)
        button.Parent = container

        button.MouseButton1Click:Connect(function()
            local value = tonumber(input.Text)
            if value then
                callback(value)
            end
        end)
    end

    local funContainer = containers["Fun"]
    createInputButtonPair(funContainer, "Speed:", "16", function(val)
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.WalkSpeed = val
        end
    end)

    createInputButtonPair(funContainer, "Jump Power:", "50", function(val)
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.JumpPower = val
        end
    end)

    -- ==========================
    -- MISC: Speed, Set Position, and Teleport
    -- ==========================
    local miscContainer = containers["Misc"]

    -- Speed in Misc
    createInputButtonPair(miscContainer, "WalkSpeed:", "16", function(val)
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.WalkSpeed = val
        end
    end)

    -- Set Position Inputs
    local positionLabel = Instance.new("TextLabel")
    positionLabel.Size = UDim2.new(0, 100, 0, 20)
    positionLabel.Position = UDim2.new(0, 10, 0, 80)
    positionLabel.Text = "Set Position:"
    positionLabel.TextColor3 = Color3.new(1,1,1)
    positionLabel.BackgroundTransparency = 1
    positionLabel.Parent = miscContainer

    local xInput = Instance.new("TextBox")
    xInput.Size = UDim2.new(0, 80, 0, 20)
    xInput.Position = UDim2.new(0, 10, 0, 110)
    xInput.Text = "0"
    xInput.PlaceholderText = "X"
    xInput.Parent = miscContainer

    local yInput = Instance.new("TextBox")
    yInput.Size = UDim2.new(0, 80, 0, 20)
    yInput.Position = UDim2.new(0, 100, 0, 110)
    yInput.Text = "0"
    yInput.PlaceholderText = "Y"
    yInput.Parent = miscContainer

    local zInput = Instance.new("TextBox")
    zInput.Size = UDim2.new(0, 80, 0, 20)
    zInput.Position = UDim2.new(0, 190, 0, 110)
    zInput.Text = "0"
    zInput.PlaceholderText = "Z"
    zInput.Parent = miscContainer

    local savePosition = Vector3.new(0,0,0) -- store position

    -- Button to set current position
    local setPositionBtn = Instance.new("TextButton")
    setPositionBtn.Size = UDim2.new(0, 150, 0, 25)
    setPositionBtn.Position = UDim2.new(0, 10, 0, 140)
    setPositionBtn.Text = "Set Pos to Stand"
    setPositionBtn.BackgroundColor3 = Color3.fromRGB(70,70,70)
    setPositionBtn.TextColor3 = Color3.new(1,1,1)
    setPositionBtn.Parent = miscContainer

    setPositionBtn.MouseButton1Click:Connect(function()
        if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local hrp = player.Character.HumanoidRootPart
            local pos = hrp.Position
            xInput.Text = tostring(math.floor(pos.X))
            yInput.Text = tostring(math.floor(pos.Y))
            zInput.Text = tostring(math.floor(pos.Z))
            -- Save position
            savePosition = Vector3.new(pos.X, pos.Y, pos.Z)
        end
    end)

    -- Teleport button
    local teleportBtn = Instance.new("TextButton")
    teleportBtn.Size = UDim2.new(0, 100, 0, 25)
    teleportBtn.Position = UDim2.new(0, 10, 0, 180)
    teleportBtn.Text = "Teleport"
    teleportBtn.BackgroundColor3 = Color3.fromRGB(70,70,70)
    teleportBtn.TextColor3 = Color3.new(1,1,1)
    teleportBtn.Parent = miscContainer

    teleportBtn.MouseButton1Click:Connect(function()
        local x = tonumber(xInput.Text)
        local y = tonumber(yInput.Text)
        local z = tonumber(zInput.Text)
        if x and y and z and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            player.Character.HumanoidRootPart.CFrame = CFrame.new(x, y, z)
        end
    end)
end

-- Connect to respawn
player.CharacterAdded:Connect(function()
    wait(1) -- wait for character to load
    createUI()
end)

-- Initial call
createUI()
            print("Escape Tsunami script executed.")
            -- Example:
           
        end,
        ["Steal a Brainrot Modded"] = function()
            print("Steal a Brainrot Modded script executed.")
           loadstring(game:HttpGet("https://rawscripts.net/raw/Steal-A-Brainrots:-BEST-EDITION!-Steal-a-brainrot-modded-op-58689"))()
        end,
        ["699 AIMBOT"] = function()
    print("699 AIMBOT script executed.")
    local Rayfield = loadstring(game:HttpGet("https://sirius.menu/rayfield"))()
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Camera = workspace.CurrentCamera
local LocalPlayer = Players.LocalPlayer
local workspace = workspace

-- Create main window
local Window = Rayfield:CreateWindow({
    Name = "699 AIMBOT",
    LoadingTitle = "699 AIMBOT",
    LoadingSubtitle = "Ultimate Script by Rains Coders",
    ConfigurationSaving = { Enabled = false }
})

-- ================== VARIABLES ==================
local aimAssist = false
local aimSmooth = 0.15
local HitboxSize = 10
local ShowESP = false
local ShowFOV = false
local FOVRadius = 150
local AimbotLock = false
local SilentAim = false

local flyMode = false
local flySpeed = 50
local jumpPower = 50
local walkSpeed = 16
local gravityValue = 196.2
local skyID = "rbxassetid://123456789" -- default sky

-- ================== UI TABS ==================
local AimTab = Window:CreateTab("Aim & Combat", 4483362458)
local VisualsTab = Window:CreateTab("Visuals", 4483362458)
local SettingsTab = Window:CreateTab("Settings", 4483362458)
local ExtraTab = Window:CreateTab("Extra", 4483362458)

-- === Aim & Combat Controls ===
AimTab:CreateToggle({ 
    Name = "Enable Aim Assist (Players)", 
    CurrentValue = false, 
    Callback = function(v) aimAssist = v end
})
AimTab:CreateSlider({ 
    Name = "Aim Smoothness", 
    Range = {1, 100}, 
    Increment = 1, 
    CurrentValue = 15, 
    Callback = function(v) aimSmooth = v/100 end
})
AimTab:CreateToggle({ 
    Name = "Aimbot Lock (Lock camera on target)", 
    CurrentValue = false, 
    Callback = function(v) AimbotLock = v end
})
AimTab:CreateToggle({ 
    Name = "Silent Aim (No camera movement)", 
    CurrentValue = false, 
    Callback = function(v) SilentAim = v end
})

-- === Hitbox Visuals ===
HitboxTab = Window:CreateTab("Hitbox Visual", 4483362458)
HitboxTab:CreateSlider({ 
    Name = "Hitbox Size", 
    Range = {1, 500}, 
    Increment = 1, 
    CurrentValue = 10, 
    Callback = function(v) HitboxSize = v end
})

-- === Visuals Controls ===
VisualsTab:CreateToggle({ 
    Name = "ESP (Players)", 
    CurrentValue = false, 
    Callback = function(v) ShowESP = v end
})
VisualsTab:CreateToggle({ 
    Name = "Show FOV Circle", 
    CurrentValue = false, 
    Callback = function(v) 
        ShowFOV = v
        circle.Visible = v
    end
})
VisualsTab:CreateSlider({ 
    Name = "FOV Radius", 
    Range = {50, 500}, 
    Increment = 5, 
    CurrentValue = FOVRadius, 
    Callback = function(v) 
        FOVRadius = v
        circle.Radius = v
    end
})

-- === Settings Controls ===
SettingsTab:CreateKeybind({ 
    Name = "Toggle UI", 
    CurrentKeybind = "RightShift", 
    HoldToInteract = false, 
    Callback = function() Rayfield:Toggle() end
})

-- === Extra Controls (Fly, Sky, Movement) ===
ExtraTab:CreateSlider({
    Name = "Fly Speed",
    Range = {10, 200},
    Increment = 1,
    CurrentValue = flySpeed,
    Callback = function(v) flySpeed = v end
})

ExtraTab:CreateSlider({
    Name = "Jump Power",
    Range = {10, 200},
    Increment = 1,
    CurrentValue = jumpPower,
    Callback = function(v)
        jumpPower = v
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Humanoid") then
            LocalPlayer.Character.Humanoid.JumpPower = v
        end
    end
})

ExtraTab:CreateSlider({
    Name = "Walk Speed",
    Range = {16, 100},
    Increment = 1,
    CurrentValue = walkSpeed,
    Callback = function(v)
        walkSpeed = v
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Humanoid") then
            LocalPlayer.Character.Humanoid.WalkSpeed = v
        end
    end
})

ExtraTab:CreateSlider({
    Name = "Gravity",
    Range = {0, 300},
    Increment = 1,
    CurrentValue = gravityValue,
    Callback = function(v)
        gravityValue = v
        workspace.Gravity = v
    end
})

ExtraTab:CreateButton({
    Name = "Toggle Fly",
    Callback = function()
        flyMode = not flyMode
        if flyMode then
            spawn(function()
                while flyMode do
                    local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                    if hrp then
                        local moveVec = Vector3.new(0,0,0)
                        if UserInputService:IsKeyDown(Enum.KeyCode.W) then
                            moveVec = moveVec + Camera.CFrame.LookVector
                        end
                        if UserInputService:IsKeyDown(Enum.KeyCode.S) then
                            moveVec = moveVec - Camera.CFrame.LookVector
                        end
                        if UserInputService:IsKeyDown(Enum.KeyCode.A) then
                            moveVec = moveVec - Camera.CFrame.RightVector
                        end
                        if UserInputService:IsKeyDown(Enum.KeyCode.D) then
                            moveVec = moveVec + Camera.CFrame.RightVector
                        end
                        if UserInputService:IsKeyDown(Enum.KeyCode.Space) then
                            moveVec = moveVec + Vector3.new(0,1,0)
                        end
                        hrp.Velocity = moveVec * flySpeed
                    end
                    wait(0.1)
                end
            end)
        end
    end
})

ExtraTab:CreateButton({
    Name = "Change Sky ID",
    Callback = function()
        local inputGui = Instance.new("ScreenGui", game.CoreGui)
        local frame = Instance.new("Frame", inputGui)
        frame.Size = UDim2.new(0, 300, 0, 100)
        frame.Position = UDim2.new(0.5, -150, 0.5, -50)
        local textbox = Instance.new("TextBox", frame)
        textbox.Size = UDim2.new(1, -20, 0, 40)
        textbox.Position = UDim2.new(0, 10, 0, 10)
        textbox.PlaceholderText = "Enter Sky ID"
        local btn = Instance.new("TextButton", frame)
        btn.Size = UDim2.new(1, -20, 0, 40)
        btn.Position = UDim2.new(0, 10, 0, 50)
        btn.Text = "Set Sky"
        btn.MouseButton1Click:Connect(function()
            local skyID = textbox.Text
            for _, v in pairs(workspace:GetChildren()) do
                if v:IsA("Sky") then v:Destroy() end
            end
            local sky = Instance.new("Sky", workspace)
            sky.SkyboxBk = skyID
            sky.SkyboxFt = skyID
            sky.SkyboxLf = skyID
            sky.SkyboxRt = skyID
            sky.SkyboxUp = skyID
            sky.SkyboxDn = skyID
            inputGui:Destroy()
        end)
    end
})

-- ================== DRAWING AND ESP ==================
local circle = Drawing.new("Circle")
circle.Thickness = 2
circle.NumSides = 64
circle.Radius = FOVRadius
circle.Visible = false
circle.Color = Color3.fromRGB(255,255,255)
circle.Filled = false

local espCache = {}

local function updateESP()
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            if ShowESP and not espCache[player] then
                local adornment = Instance.new("BoxHandleAdornment")
                adornment.Size = Vector3.new(HitboxSize, HitboxSize*1.5, HitboxSize)
                adornment.Adornee = player.Character.HumanoidRootPart
                adornment.AlwaysOnTop = true
                adornment.ZIndex = 5
                adornment.Transparency = 0.5
                adornment.Color3 = Color3.fromRGB(255,0,0)
                adornment.Parent = workspace
                espCache[player] = adornment
            elseif not ShowESP and espCache[player] then
                espCache[player]:Destroy()
                espCache[player] = nil
            elseif espCache[player] then
                espCache[player].Size = Vector3.new(HitboxSize, HitboxSize*1.5, HitboxSize)
            end
        end
    end
end

local function getClosestPlayer()
    local closest, minDist = nil, math.huge
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local hrp = player.Character.HumanoidRootPart
            local screenPos, onScreen = Camera:WorldToViewportPoint(hrp.Position)
            if onScreen then
                local dist = (Vector2.new(screenPos.X, screenPos.Y) - Vector2.new(Camera.ViewportSize.X/2, Camera.ViewportSize.Y/2)).Magnitude
                if dist < minDist and dist < FOVRadius then
                    minDist = dist
                    closest = hrp
                end
            end
        end
    end
    return closest
end

RunService.RenderStepped:Connect(function()
    -- Update ESP
    updateESP()

    -- Update FOV circle
    circle.Position = Vector2.new(Camera.ViewportSize.X/2, Camera.ViewportSize.Y/2)
    circle.Radius = FOVRadius
    circle.Visible = ShowFOV

    -- Aim & Target Lock
    if aimAssist then
        local targetHRP = getClosestPlayer()
        if targetHRP then
            local targetPos, onScreen = Camera:WorldToViewportPoint(targetHRP.Position)
            if onScreen then
                local currentCF = Camera.CFrame
                local targetCF = CFrame.new(currentCF.Position, targetHRP.Position)
                if AimbotLock then
                    Camera.CFrame = targetCF
                else
                    Camera.CFrame = currentCF:Lerp(targetCF, aimSmooth)
                end
            end
        end
    end
end)
end,
    }

    -- Function to create a script button
    local function createScriptButton(name, callback)
        local btn = Instance.new("TextButton")
        btn.Size = UDim2.new(1, 0, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
        btn.TextColor3 = Color3.new(1, 1, 1)
        btn.Font = Enum.Font.SourceSansBold
        btn.TextSize = 20
        btn.Text = name
        btn.Parent = scriptList

        btn.MouseButton1Click:Connect(callback)
        return btn
    end

    -- Store all buttons to filter by search
    local scriptButtons = {}

    -- Create all script buttons initially
    for name, callback in pairs(scripts) do
        local btn = createScriptButton(name, callback)
        table.insert(scriptButtons, {button = btn, name = name:lower()})
    end

    -- Update scrolling frame canvas size based on content
    local function updateCanvasSize()
        local contentSize = uiListLayout.AbsoluteContentSize
        scriptList.CanvasSize = UDim2.new(0, 0, 0, contentSize.Y + 10)
    end
    uiListLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(updateCanvasSize)
    updateCanvasSize()

    -- Search filter function
    searchBox:GetPropertyChangedSignal("Text"):Connect(function()
        local searchTerm = searchBox.Text:lower()
        for _, entry in pairs(scriptButtons) do
            local visible = entry.name:find(searchTerm) ~= nil
            entry.button.Visible = visible
        end
        updateCanvasSize()
    end)
end

-- Connect character added to recreate UI on respawn
player.CharacterAdded:Connect(function()
    wait(1)
    if player.PlayerGui:FindFirstChild("699 Hub") then
        return
    end
    createUI()
end)

-- Key submit button logic
submitButton.MouseButton1Click:Connect(function()
    local enteredKey = keyInput.Text
    if enteredKey == "1234" then
        keyPrompt:Destroy()
        createUI()
    else
        player:Kick("Incorrect key.")
    end
end)
