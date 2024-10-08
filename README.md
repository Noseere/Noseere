-- Carga la biblioteca de IU
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/UI-Library-Link"))()
local Window = Library.CreateLib("Noseere Hub", "DarkTheme")
local Tab = Window:NewTab("Skywars")
local Section = Tab:NewSection("Main")

-- Variables importantes
local oresToFarm = {"Diamond Ore", "Emerald Ore", "Gold Ore", "Coal Ore"} -- Tipos de ores
local player = game.Players.LocalPlayer
local workspace = game:GetService("Workspace")

-- Función para detectar y farmear ores
local function farmOres()
    while true do
        for _, oreName in ipairs(oresToFarm) do
            for _, ore in pairs(workspace:GetChildren()) do
                if ore:IsA("Part") and ore.Name == oreName and (ore.Position - player.Character.HumanoidRootPart.Position).magnitude < 10 then
                    player.Character.HumanoidRootPart.CFrame = ore.CFrame -- Moverse hacia el ore
                    wait(0.5) -- Espera un poco antes de "minar"
                    ore:Destroy() -- Simulación de minería
                end
            end
        end
        wait(2) -- Espera entre cada ciclo de farmeo
    end
end

-- Botón de Auto Farm
Section:NewButton("Auto farm", "Farmea automáticamente los ores", function()
    print("Auto farm activado")
    farmOres() -- Ejecuta la función de farmear ores
end)

-- Función para cerrar la ventana
Section:NewButton("Cerrar", "Cierra la ventana", function()
    Library:Close()
end)
