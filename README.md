local Creator = loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Utilities/main/Doors%20Entity%20Spawner/Source.lua"))()

-- Create entity
local entity = Creator.createEntity({
    CustomName = "Dread", -- Custom name of your entity
    Model = "rbxassetid://12805768832", -- Can be GitHub file or rbxassetid
    Speed = 600, -- Percentage, 100 = default Rush speed
    DelayTime = 30, -- Time before starting cycles (seconds)
    HeightOffset = 6,
    CanKill = true,
    KillRange = 10000,
    BreakLights = true,
    BackwardsMovement = false,
    FlickerLights = {
        true, -- Enabled/Disabled
        27, -- Time (seconds)
    },
    Cycles = {
        Min = 1,
        Max = 3,
        WaitTime = 2,
    },
    CamShake = {
        6, -- Enabled/Disabled
        {10.5, 20, 0.1, 1}, -- Shake values (don't change if you don't know)
        100, -- Shake start distance (from Entity to you)
    },
    Jumpscare = {
        true, -- Enabled/Disabled
        {
            Image1 = "rbxassetid:// 8126977772", -- Image1 url
            Image2 = "rbxassetid:// 8126977772", -- Image2 url
            Shake = true,
            Sound1 = {
                6205670536, -- SoundId
                { Volume = 0.5 }, -- Sound properties
            },
            Sound2 = {
                6205670536, -- SoundId
                { Volume = 0.5 }, -- Sound properties
            },
            Flashing = {
                true, -- Enabled/Disabled
                Color3.fromRGB(255, 255, 255), -- Color
            },
            Tease = {
                true, -- Enabled/Disabled
                Min = 1,
                Max = 3,
            },
        },
    },
    CustomDialog = {"You can", "put your", "custom death", "message here."}, -- Custom death message
})

-----[[ Advanced ]]-----
entity.Debug.OnEntitySpawned = function(entityTable)
    print("Entity has spawned:", entityTable.Model)
end

entity.Debug.OnEntityDespawned = function(entityTable)
    print("Entity has despawned:", entityTable.Model)
end

entity.Debug.OnEntityStartMoving = function(entityTable)
    print("Entity has started moving:", entityTable.Model)
end

entity.Debug.OnEntityFinishedRebound = function(entityTable)
    print("Entity has finished rebound:", entityTable.Model)
end

entity.Debug.OnEntityEnteredRoom = function(entityTable, room)
    print("Entity:", entityTable.Model, "has entered room:", room)
end

entity.Debug.OnLookAtEntity = function(entityTable)
    print("Player has looked at entity:", entityTable.Model)
end

entity.Debug.OnDeath = function(entityTable)
    warn("Player has died.")
end
------------------------

-- Run the created entity
Creator.runEntity(entity)
