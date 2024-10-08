-- Carga la biblioteca de IU
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/UI-Library-Link"))()
local Window = Library.CreateLib("Noseere Hub", "DarkTheme")
local Tab = Window:NewTab("Skywars")
local Section = Tab:NewSection("Main")

-- Variables importantes
local oresToFarm = {"Diamond", "Emerald", "Gold", "Coal"}  -- Tipos de ores
local player = game.Players.LocalPlayer
local workspace = game:GetService("Workspace")

-- Función para detectar ores
local function farmOres()
    for _, oreType in pairs(oresToFarm) do
        for _, ore in pairs(workspace:GetChildren()) do
            if ore:IsA("Part") and ore.Name == oreType then
                player.Character.HumanoidRootPart.CFrame = ore.CFrame  -- Mueve al jugador al ore
                wait(0.5)  -- Espera un poco antes de "minar"
                ore:Destroy()  -- Simulación de minería (podrías reemplazar con otra acción)
            end
        end
    end
end

-- Botón de Auto Farm
Section:NewButton("Auto farm", "Farmea automáticamente los ores", function()
    print("Auto farm activado")
    while true do
        farmOres()
        wait(2)  -- Tiempo de espera entre cada ciclo de farmeo
    end
end)
