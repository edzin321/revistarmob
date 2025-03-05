local TextChatService = game:GetService("TextChatService")

-- Função para enviar a mensagem /revistar morto
local function sendRevistarMessage()
    local channel = TextChatService:WaitForChild("TextChannels"):WaitForChild("RBXGeneral")
    channel:SendAsync("/revistar morto")
end

-- Cria a interface
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local CloseButton = Instance.new("TextButton")
local RevistarButton = Instance.new("TextButton")
local Title = Instance.new("TextLabel")
local Corner = Instance.new("UICorner")  -- Para bordas arredondadas no Frame
local CloseButtonCorner = Instance.new("UICorner")  -- Para bordas arredondadas no botão Fechar (X)
local RevistarButtonCorner = Instance.new("UICorner")  -- Para bordas arredondadas no botão Revistar

ScreenGui.Name = "RevistarUI"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Estilo do Frame
Frame.Size = UDim2.new(0, 300, 0, 150)
Frame.Position = UDim2.new(0.5, -150, 0.5, -75)
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)  -- Cor de fundo preta
Frame.BorderSizePixel = 0
Frame.BackgroundTransparency = 0.1
Frame.Active = true
Frame.Draggable = true

-- Adiciona bordas arredondadas no Frame
Corner.Parent = Frame
Corner.CornerRadius = UDim.new(0, 15)  -- Arredondando os cantos do Frame

-- Título
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Position = UDim2.new(0, 0, 0, 0)
Title.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Title.Text = "Mini Menu"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 18

-- Botão Fechar (X sem fundo, apenas o "X")
CloseButton.Size = UDim2.new(0, 30, 0, 30)
CloseButton.Position = UDim2.new(1, -30, 0, 0)
CloseButton.BackgroundTransparency = 1  -- Sem fundo
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)  -- Cor do texto branca
CloseButton.Font = Enum.Font.SourceSansBold
CloseButton.TextSize = 18
CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- Adiciona bordas arredondadas no botão Fechar (X)
CloseButtonCorner.Parent = CloseButton
CloseButtonCorner.CornerRadius = UDim.new(1, 0)  -- Torna o botão redondo

-- Botão Revistar (cinza claro e redondo)
RevistarButton.Size = UDim2.new(0.8, 0, 0.4, 0)
RevistarButton.Position = UDim2.new(0.1, 0, 0.5, -30)
RevistarButton.BackgroundColor3 = Color3.fromRGB(211, 211, 211)  -- Cor cinza claro
RevistarButton.Text = "manda /revistar morto"
RevistarButton.TextColor3 = Color3.fromRGB(0, 0, 0)  -- Cor do texto preta para contraste
RevistarButton.Font = Enum.Font.SourceSansBold
RevistarButton.TextSize = 20
RevistarButton.AutoButtonColor = true
RevistarButton.MouseButton1Click:Connect(function()
    sendRevistarMessage()
end)

-- Adiciona bordas arredondadas no botão Revistar
RevistarButtonCorner.Parent = RevistarButton
RevistarButtonCorner.CornerRadius = UDim.new(1, 0)  -- Torna o botão redondo

-- Adiciona os elementos ao frame
Frame.Parent = ScreenGui
Title.Parent = Frame
CloseButton.Parent = Frame
RevistarButton.Parent = Frame
