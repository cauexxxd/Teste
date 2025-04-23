-- Cafex Hub Mobile - Capítulo 1 com CHAVE
-- Senha: cauedev

local senhaCorreta = "cauedev"
local acessoLiberado = false

-- GUI de Login
local gui = Instance.new("ScreenGui", game.CoreGui)
gui.Name = "CafexLogin"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)

local box = Instance.new("TextBox", frame)
box.Size = UDim2.new(0.8, 0, 0, 40)
box.Position = UDim2.new(0.1, 0, 0.2, 0)
box.PlaceholderText = "Digite a chave..."
box.Text = ""
box.TextScaled = true
box.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
box.TextColor3 = Color3.new(1,1,1)

local btn = Instance.new("TextButton", frame)
btn.Size = UDim2.new(0.8, 0, 0, 40)
btn.Position = UDim2.new(0.1, 0, 0.6, 0)
btn.Text = "Entrar"
btn.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
btn.TextColor3 = Color3.new(1,1,1)
btn.TextScaled = true

local erro = Instance.new("TextLabel", frame)
erro.Size = UDim2.new(1, 0, 0, 20)
erro.Position = UDim2.new(0, 0, 0.9, 0)
erro.Text = ""
erro.TextColor3 = Color3.new(1, 0, 0)
erro.BackgroundTransparency = 1
erro.TextScaled = true

btn.MouseButton1Click:Connect(function()
	if box.Text == senhaCorreta then
		gui:Destroy()
		acessoLiberado = true
	else
		erro.Text = "Senha incorreta!"
	end
end)

-- AGUARDAR ACESSO
repeat wait() until acessoLiberado

-- CAFEX HUB MOBILE - EXEMPLO FUNCIONAL
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local gui2 = Instance.new("ScreenGui", game.CoreGui)
gui2.Name = "CafexHubMobile"

local main = Instance.new("Frame", gui2)
main.Size = UDim2.new(0, 250, 0, 150)
main.Position = UDim2.new(0.5, -125, 0.5, -75)
main.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

local titulo = Instance.new("TextLabel", main)
titulo.Size = UDim2.new(1, 0, 0.3, 0)
titulo.Position = UDim2.new(0, 0, 0, 0)
titulo.Text = "Cafex Hub - Capítulo 1"
titulo.TextColor3 = Color3.new(1, 1, 1)
titulo.BackgroundTransparency = 1
titulo.TextScaled = true

local botao = Instance.new("TextButton", main)
botao.Size = UDim2.new(0.8, 0, 0.3, 0)
botao.Position = UDim2.new(0.1, 0, 0.5, 0)
botao.Text = "Clique aqui!"
botao.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
botao.TextColor3 = Color3.new(1, 1, 1)
botao.TextScaled = true

botao.MouseButton1Click:Connect(function()
	LocalPlayer:Kick("Você clicou no botão do Capítulo 1!")
end)
