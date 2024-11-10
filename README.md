-- Script para conseguir todos los pases de Brookhaven de la actualización de Halloween

-- Mensaje de advertencia
print("¡Advertencia! Este script puede violar los términos de servicio de Roblox. Úsalo bajo tu propio riesgo.")

-- Función para obtener los pases
function obtenerPases()
    -- Asegúrate de que el juego esté cargado
    repeat wait() until game:IsLoaded()

    -- Acceder a los servicios necesarios
    local Players = game:GetService("Players")
    local player = Players.LocalPlayer

    -- Acceder a la tienda de pases
    local tienda = game:GetService("ReplicatedStorage"):WaitForChild("Pases")

    -- Lista de pases de Halloween
    local pasesHalloween = {
        "PaseDeHalloween1",
        "PaseDeHalloween2",
        "PaseDeHalloween3",
        -- Agrega más pases según sea necesario
    }

    -- Comprar cada pase
    for _, pase in ipairs(pasesHalloween) do
        local paseObjeto = tienda:FindFirstChild(pase)
        if paseObjeto then
            -- Intentar comprar el pase
            local exito, mensaje = pcall(function()
                paseObjeto:FireServer()
            end)
            if exito then
                print("Comprado: " .. pase)
            else
                print("Error al comprar: " .. mensaje)
            end
        else
            print("Pase no encontrado: " .. pase)
        end
    end
end

-- Ejecutar la función
obtenerPases()
