-- Fly Script Mobile - Cafex (Mad City / Delta Executor)
local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = char:WaitForChild("HumanoidRootPart")

local flying = false
local speed = 5
local bodyGyro, bodyVelocity

-- Função de ativar fly
function startFly()
    bodyGyro = Instance.new("BodyGyro")
    bodyGyro.P = 9e4
    bodyGyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
    bodyGyro.cframe = humanoidRootPart.CFrame
    bodyGyro.Parent = humanoidRootPart

    bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.velocity = Vector3.new(0, 0, 0)
    bodyVelocity.maxForce = Vector3.new(9e9, 9e9, 9e9)
    bodyVelocity.Parent = humanoidRootPart

    flying = true

    game:GetService("RunService").RenderStepped:Connect(function()
        if flying then
            bodyVelocity.velocity = workspace.CurrentCamera.CFrame.lookVector * speed
            bodyGyro.cframe = workspace.CurrentCamera.CFrame
        end
    end)
end

-- Função de parar fly
function stopFly()
    flying = false
    if bodyGyro then bodyGyro:Destroy() end
    if bodyVelocity then bodyVelocity:Destroy() end
end

-- Criar interface Cafex
local CafexGUI = Instance.new("ScreenGui", game.CoreGui)
CafexGUI.Name = "Cafex"

local Button = Instance.new("TextButton", CafexGUI)
Button.Size = UDim2.new(0, 140, 0, 50)
Button.Position = UDim2.new(0.5, -70, 0.9, 0)
Button.Text = "Cafex: Ativar Fly"
Button.BackgroundColor3 = Color3.fromRGB(0, 100, 255)
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextScaled = true
Button.Visible = true
Button.BorderSizePixel = 2

-- Alternar fly ao clicar
Button.MouseButton1Click:Connect(function()
    if flying then
        stopFly()
        Button.Text = "Cafex: Ativar Fly"
    else
        startFly()
        Button.Text = "Cafex: Desativar Fly"
    end
end)

print("Cafex - Fly Script Mobile carregado.")
