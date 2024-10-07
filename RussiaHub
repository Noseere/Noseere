-- Script para Roblox Skywars (Clásico) con UI estilo "WE<3RussiaHub"

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

-- Crear ScreenGui para UI
local screenGui = Instance.new("ScreenGui", player.PlayerGui)
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Size = UDim2.new(0, 300, 0, 400)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -200)
mainFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

-- Crear barra lateral para categorías (como en WE<3RussiaHub)
local sideBar = Instance.new("Frame", mainFrame)
sideBar.Size = UDim2.new(0, 80, 0, 400)
sideBar.Position = UDim2.new(0, 0, 0, 0)
sideBar.BackgroundColor3 = Color3.fromRGB(255, 0, 0)

-- Título de la UI
local titleLabel = Instance.new("TextLabel", mainFrame)
titleLabel.Size = UDim2.new(0, 220, 0, 50)
titleLabel.Position = UDim2.new(0, 80, 0, 0)
titleLabel.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
titleLabel.Text = "WE<3RussiaHub"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.Font = Enum.Font.SourceSans
titleLabel.TextSize = 24

-- Botones en la barra lateral
local buttons = {
    "Main",
    "Player",
    "Teleports",
    "Buys",
    "Armor Sets"
}

for i, btnName in ipairs(buttons) do
    local button = Instance.new("TextButton", sideBar)
    button.Size = UDim2.new(0, 80, 0, 40)
    button.Position = UDim2.new(0, 0, 0, (i-1)*50)
    button.Text = btnName
    button.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
end

-- Botones en el menú principal
local mainScripts = {
    {"Auto Farm", autoFarm},
    {"Kill Player", killAura},
    {"Anti Void", antiVoid},
    {"Auto Heal", autoHeal},
    {"Auto Buy Powers", autoBuyPowers},
    {"Infinite Jump", infiniteJump}
}

for i, scriptData in ipairs(mainScripts) do
    local scriptButton = Instance.new("TextButton", mainFrame)
    scriptButton.Size = UDim2.new(0, 220, 0, 40)
    scriptButton.Position = UDim2.new(0, 80, 0, (i-1)*50 + 60)
    scriptButton.Text = scriptData[1]
    scriptButton.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
    scriptButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    scriptButton.MouseButton1Click:Connect(scriptData[2]) -- Conectar con la función
end

-- Función para Auto Farm (recolectar ores)
function autoFarm()
    while true do
        for _, ore in pairs(workspace:GetChildren()) do
            if ore.Name == "Diamond" or ore.Name == "Emerald" or ore.Name == "Gold" or ore.Name == "Coal" then
                ore:Destroy()  -- Recolectar automáticamente
            end
        end
        wait(1)
    end
end

-- Función para Kill Aura (atacar automáticamente)
function killAura()
    while true do
        for _, enemy in pairs(workspace:GetChildren()) do
            if enemy:IsA("Player") and (character.HumanoidRootPart.Position - enemy.HumanoidRootPart.Position).Magnitude < 50 then
                -- Lógica para atacar
            end
        end
        wait(0.5)
    end
end

-- Función Anti-Void (evitar caer al vacío)
function antiVoid()
    local lastSafePosition
    while true do
        if character.HumanoidRootPart.Position.Y < -10 then
            if lastSafePosition then
                character.HumanoidRootPart.CFrame = lastSafePosition -- Regresar al último lugar seguro
            end
        else
            lastSafePosition = character.HumanoidRootPart.CFrame -- Guardar última posición segura
        end
        wait(1)
    end
end

-- Función Auto Heal (curarse con poción de vida)
function autoHeal()
    while true do
        if humanoid.Health < humanoid.MaxHealth * 0.3 then
            local healthPotion = player.Backpack:FindFirstChild("HealthPotion")
            if healthPotion then
                healthPotion:Activate() -- Usar la poción automáticamente
            end
        end
        wait(1)
    end
end

-- Función Auto Buy Powers (comprar poderes automáticamente)
function autoBuyPowers()
    -- Lógica para comprar poderes (escudo, vida, velocidad, salto alto)
end

-- Función para Infinite Jump (saltar infinitamente)
function infiniteJump()
    player.Character.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
end
