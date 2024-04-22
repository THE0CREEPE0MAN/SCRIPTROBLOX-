local IsOpen = true -- Variable indiquant si la fenêtre est ouverte ou fermée

local closeFunc = function()
    IsOpen = false
    if rainbowAvatarEnabled then
        disableRainbowAvatar()
    end
    if rainbowNameEnabled then
        disableRainbowName()
    end
    if rainbowBioEnabled then
        disableRainbowBio()
    end
    if RainbowCarEnabled then
        disableRainbowCar()
    end
    if RainbowHouseEnabled then
        disableRainbowHouse()
    end
    setRolePlayName("") -- Efface le nom de rôle-play
    os.exit() -- Arrête complètement le script
end

game:GetService("CoreGui").ChildRemoved:Connect(function(child)
    if child.Name == "ScreenGui" and not IsOpen then
        closeFunc()
    end
end)

loadstring(game:HttpGet("https://raw.githubusercontent.com/REDzHUB/LibraryV2/main/redzLib"))()

MakeWindow({
    Hub = {
        Title = "Kings Hub v1 Brookhaven 🏡🌲",
        Animation = "Chargement du script.."
    },
    Key = {
        KeySystem = false,
        Title = "Key System",
        Description = "",
        KeyLink = "",
        Keys = {"1234"},
        Notifi = {
            Notifications = true,
            CorrectKey = "Chargement du script...",
            Incorrectkey = "Le clé est incorrecte",
            CopyKeyLink = "Copier dans le presse-papier"
        }
    }
})

MinimizeButton({
    Image = "",
    Size = {40, 40},
    Color = Color3.fromRGB(0, 0, 0),
    Corner = true,
    Stroke = true,
    StrokeColor = Color3.fromRGB(255, 0, 0)
})

local Main = MakeTab({Name = "Joueur"})

local section = AddSection(Main, {"Rainbow Section"})

-- Rainbow Avatar
local rainbowAvatarEnabled = false
local rainbowAvatarColors = {
    "Really blue",
    "Toothpaste",
    "Lime green",
    "New Yeller",
    "Really red",
    "Hot pink",
    "Magenta",
    "Institutional white",
    "Really black"
}
local currentAvatarColorIndex = 1

local function changeAvatarColor(color)
    local args = {
        [1] = "skintone",
        [2] = color
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Updat1eAvata1r"):FireServer(unpack(args))
end

local function enableRainbowAvatar()
    rainbowAvatarEnabled = true
    while rainbowAvatarEnabled do
        changeAvatarColor(rainbowAvatarColors[currentAvatarColorIndex])
        currentAvatarColorIndex = (currentAvatarColorIndex % #rainbowAvatarColors) + 1
        wait(0.5)
    end
end

local function disableRainbowAvatar()
    rainbowAvatarEnabled = false
    currentAvatarColorIndex = 1
end

local JoueurToggleAvatar = AddToggle(Main, {
    Name = "Rainbow Avatar",
    Default = false,
    Callback = function(Value)
        if Value then
            enableRainbowAvatar()
        else
            disableRainbowAvatar()
        end
    end
})

-- Rainbow Name
local rainbowNameEnabled = false
local RPNameColors = {
    Color3.new(1, 1, 1),
    Color3.new(0, 0.992, 1),
    Color3.new(0.199, 1, 0),
    Color3.new(0.975, 1, 0),
    Color3.new(1, 0, 0.0407),
    Color3.new(1, 0, 0.721),
    Color3.new(0.584, 0, 1),
}
local currentNameColorIndex = 1

local function setRolePlayNameColor(color)
    local args = {
        [1] = "PickingRPNameColor",
        [2] = color
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eColo1r"):FireServer(unpack(args))
end

local function enableRainbowName()
    rainbowNameEnabled = true
    while rainbowNameEnabled do
        setRolePlayNameColor(RPNameColors[currentNameColorIndex])
        currentNameColorIndex = (currentNameColorIndex % #RPNameColors) + 1
        wait(0.5)
    end
end

local function disableRainbowName()
    rainbowNameEnabled = false
    currentNameColorIndex = 1
end

local JoueurToggleRPNameRainbow = AddToggle(Main, {
    Name = "Rainbow Name",
    Default = false,
    Callback = function(Value)
        if Value then
            enableRainbowName()
        else
            disableRainbowName()
        end
    end
})

-- Rainbow Bio
local rainbowBioEnabled = false
local RPBioColors = {
    Color3.new(1, 0.018847346305847168, 0),
    Color3.new(0.9922822713851929, 0, 1),
    Color3.new(0.5338655710220337, 0, 1),
    Color3.new(0, 0.05418801307678223, 1),
    Color3.new(0, 0.9262446165084839, 1),
    Color3.new(0, 1, 0.2555587887763977),
    Color3.new(0.8795322179794312, 1, 0)
}
local currentBioColorIndex = 1

local function setRolePlayBioColor(color)
    local args = {
        [1] = "PickingRPBioColor",
        [2] = color
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPNam1eColo1r"):FireServer(unpack(args))
end

local function enableRainbowBio()
    rainbowBioEnabled = true
    while rainbowBioEnabled do
        setRolePlayBioColor(RPBioColors[currentBioColorIndex])
        currentBioColorIndex = (currentBioColorIndex % #RPBioColors) + 1
        wait(0.5)
    end
end

local function disableRainbowBio()
    rainbowBioEnabled = false
    currentBioColorIndex = 1
end

local JoueurToggleRPBioRainbow = AddToggle(Main, {
    Name = "Rainbow Bio",
    Default = false,
    Callback = function(Value)
        if Value then
            enableRainbowBio()
        else
            disableRainbowBio()
        end
    end
})

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local function setRolePlayName(name)
    local args = {
        [1] = "RolePlayName",
        [2] = name
    }
    ReplicatedStorage:WaitForChild("RE"):WaitForChild("1RPNam1eTex1t"):FireServer(unpack(args))
end

setRolePlayName("⚒️Kings Hub⚒️")

local function setRolePlayBio(bio)
    local args = {
        [1] = "RolePlayBio",
        [2] = bio
    }
    ReplicatedStorage:WaitForChild("RE"):WaitForChild("1RPNam1eTex1t"):FireServer(unpack(args))
end

setRolePlayBio("FRIEND OF THE CREATOR")

local section = AddSection(Main, {"Taille de l'avatar et plus"})

-- Déclaration des variables
local ChangeAvatarLoopEnabled = true
local ChangeAvatarLoopOutfits = {14, 15} -- Liste des ID des tenues à utiliser
local currentOutfitIndex = 2
local ChangeAvatarLoopInterval = 4 -- Intervalle de temps en secondes entre chaque changement de tenue

-- Fonction pour changer de tenue
local function changeOutfit(outfitID)
    local args = {
        [1] = "AskingToWearOutfit",
        [2] = outfitID
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
end

-- Fonction pour activer la boucle de changement d'avatar
local function enableChangeAvatarLoop()
    ChangeAvatarLoopEnabled = true
    while ChangeAvatarLoopEnabled do
        changeOutfit(ChangeAvatarLoopOutfits[currentOutfitIndex])
        currentOutfitIndex = (currentOutfitIndex % #ChangeAvatarLoopOutfits) + 1
        wait(ChangeAvatarLoopInterval)
    end
end

-- Fonction pour désactiver la boucle de changement d'avatar
local function disableChangeAvatarLoop()
    ChangeAvatarLoopEnabled = false
    currentOutfitIndex = 1
end

-- Case à cocher pour activer/désactiver la boucle de changement d'avatar
local JoueurToggleChangeAvatarLoop = AddToggle(Main, {
    Name = "Change Avatar Loop", -- Nom de la case à cocher
    Default = false, -- Valeur par défaut (désactivée)
    Callback = function(Value)
        if Value then
            enableChangeAvatarLoop() -- Activation de la boucle de changement d'avatar
        else
            disableChangeAvatarLoop() -- Désactivation de la boucle de changement d'avatar
        end
    end
})

local ChangeAvatarSizeLoopEnabled = false

local function changeAvatarSizeLoop()
    while ChangeAvatarSizeLoopEnabled do
        local args = {
            [1] = "CharacterSizeUp",
            [2] = 1
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.95
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.9
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.8
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.75
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.7
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.65
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.6
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
        args[2] = 0.55
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clothe1s"):FireServer(unpack(args))
        wait(0.3)
    end
end

local JoueurToggleChangeAvatarSizeLoop = AddToggle(Main, {
    Name = "Change Avatar Size Loop",
    Default = false,
    Callback = function(Value)
        if Value then
            ChangeAvatarSizeLoopEnabled = true
            changeAvatarSizeLoop()
        else
            ChangeAvatarSizeLoopEnabled = false
        end
    end
})

local section = AddSection(Main, {"Maison bug"})

-- Rainbow House
local RainbowHouseEnabled = false
local RainbowHouseColors = {
    Color3.new(1, 1, 1),
    Color3.new(0.052469491958618164, 0, 1),
    Color3.new(0, 1, 0.9615281820297241),
    Color3.new(0, 1, 0.03253042697906494),
    Color3.new(0.8516436815261841, 1, 0),
    Color3.new(1, 0.5746384859085083, 0),
    Color3.new(1, 0, 0.208573579788208),
    Color3.new(1, 0, 0.8310080766677856),
    Color3.new(0.5879220962524414, 0, 1),
    Color3.new(0.3513219356536865, 0.679409921169281, 1),
    Color3.new(0.3513219356536865, 0.679409921169281, 1),
    Color3.new(0.2954559326171875, 1, 0.9818400144577026),
    Color3.new(0.10693556070327759, 1, 0.3617424964904785),
    Color3.new(0.8685014247894287, 1, 0.3436591625213623),
    Color3.new(1, 0.7427822351455688, 0.3774229884147644),
    Color3.new(1, 0.46761226654052734, 0.7965571880340576),
    Color3.new(0.6969243884086609, 0.5095046758651733, 1)
}
local currentHouseColorIndex = 1

local function changeHouseColor(color)
    local args = {
        [1] = "ColorPickHouse",
        [2] = color
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sHous1e"):FireServer(unpack(args))
end

local function enableRainbowHouse()
    RainbowHouseEnabled = true
    while RainbowHouseEnabled do
        changeHouseColor(RainbowHouseColors[currentHouseColorIndex])
        currentHouseColorIndex = (currentHouseColorIndex % #RainbowHouseColors) + 1
        wait(1)
    end
end

local function disableRainbowHouse()
    RainbowHouseEnabled = false
    currentHouseColorIndex = 1
end

local JoueurToggleRainbowHouse = AddToggle(Main, {
    Name = "Rainbow House",
    Default = false,
    Callback = function(Value)
        if Value then
            enableRainbowHouse()
        else
            disableRainbowHouse()
        end
    end
})

local BusinessNameTextBox = AddTextBox(Main, {
    Name = "Business Name",
    Default = "",
    Placeholder = "Enter new business name",
    Callback = function(Text)
        local args = {
            [1] = "BusinessName",
            [2] = Text
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPHous1eEven1t"):FireServer(unpack(args))
    end
})

-- Rainbow Bio
local RainbowBioMaisonToggle = AddToggle(Main, {
    Name = "Rainbow Bio Maison",
    Default = false,
    Callback = function(Value)
        local args = {
            [1] = "PickingBusinessNameColor",
            [2] = game:GetService("Players").LocalPlayer:WaitForChild("Color")
        }

        local event = game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1RPHous1eEven1tColo1r")

        if Value then
            -- Active la répétition pendant 0.8 seconde
            while RainbowBioMaisonToggle:GetState() do
                event:FireServer(unpack(args))
                wait(0.8)
            end
        end
    end
})

local changeCurtainsEnabled = false

local function changeCurtainsLoop()
    while changeCurtainsEnabled do
        local args = {
            [1] = "Curtains"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sHous1e"):FireServer(unpack(args))
        wait(0.5)
    end
end

local Toggle = AddToggle(Main, {
    Name = "Voler de la maison bug",
    Default = false,
    Callback = function(Value)
        changeCurtainsEnabled = Value
        if Value then
            changeCurtainsLoop()
        end
    end
})

local Toggle = AddToggle(Main, {
    Name = "Lavabos  Et Douche Maison activer/désactiver",
    Default = false,
    Callback = function(Value)
        if Value then
            local playerName = game.Players.LocalPlayer.Name
            local lavabos = {
                "WashHandsOn3" .. playerName,
                "WashHandsOn4" .. playerName,
                "ShowerOn" .. playerName,
                "WashHandsOn2" .. playerName,
                "ShowerOn2" .. playerName,
                "TubOn2" .. playerName,
                "TubOn" .. playerName,
                "WashHandsOn" .. playerName
            }
            for _, lavabo in ipairs(lavabos) do
                local args = {
                    [1] = lavabo
                }
                game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Animatio1nFir1eClien1t"):FireServer(unpack(args))
            end
          
        else
            local playerName = game.Players.LocalPlayer.Name
            local offActions = {
                "ShowerOff1",
                "ShowerOff2",
                "ShowerOff3",
                "ShowerOff4",
                "WashHandsOff1",
                "WashHandsOff2",
                "WashHandsOff3",
                "WashHandsOff4",
                "WashHandsOff5",
                "WashHandsOff6",
                "WashHandsOff",
                "ShowerOff",
            }
            for _, action in ipairs(offActions) do
                local args = {
                    [1] = action .. playerName
                }
                game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Animatio1nFir1eClien1t"):FireServer(unpack(args))
            end
           
        end
    end
})
                        
local section = AddSection(Main, {"Vehicule Transformation"})

AddButton(Main, {
    Name = "Transformation du véhicule",
    Callback = function()
        
        local argsMusiqueScooter = {
            [1] = "PickingScooterMusicText",
            [2] = "15689445424"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1NoMoto1rVehicle1s"):FireServer(unpack(argsMusiqueScooter))
        
        -- Jouer de la musique pour la transformation de la voiture
        local argsMusiqueVoiture = {
            [1] = "PickingCarMusicText",
            [2] = "15689445424"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(argsMusiqueVoiture))

        local actions = {
            { "Fire"},
            { "Smoke" },
            { "Duke" },
            { "200PlayerGiveSpeed", "100" },
            { "TurboStage", 1 },
            { "TurboStage", 2 },
            { "TurboStage", 3 },
            { "DriftingNumber", 1.1 },
            { "DriftingNumber", 1.2000000000000002 },
            { "DriftingNumber", 1.3000000000000003 },
            { "DriftingNumber", 1.4000000000000004 },
            { "DriftingNumber", 1.5000000000000004 }
        }
        
        for _, args in ipairs(actions) do
            local argDelay = args[1] == "TurboStage" and 0.1 or 0.3
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            wait(argDelay)
        end
    end
})

-- Rainbow Car
local RainbowCarEnabled = false
local RainbowCarColors = {
    Color3.new(0.048056721687316895, 0, 1),
    Color3.new(0.048056721687316895, 0, 1),
    Color3.new(0, 1, 0.9987940788269043),
    Color3.new(0, 1, 0.30482882261276245),
    Color3.new(0.8824552893638611, 1, 0),
    Color3.new(1, 0.37878429889678955, 0),
    Color3.new(1, 0, 0.07956933975219727),
    Color3.new(0.9731431007385254, 0, 1),
    Color3.new(0.40603363513946533, 0, 1),
    Color3.new(0, 0, 0)
}
local currentCarColorIndex = 1

local function changeCarColor(color)
    local args = {
        [1] = "PickingCarColor",
        [2] = color
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
end

local function enableRainbowCar()
    RainbowCarEnabled = true
    while RainbowCarEnabled do
        changeCarColor(RainbowCarColors[currentCarColorIndex])
        currentCarColorIndex = (currentCarColorIndex % #RainbowCarColors) + 1
        wait(1)
    end
end

local function disableRainbowCar()
    RainbowCarEnabled = false
    currentCarColorIndex = 1
end

local JoueurToggleRainbowCar = AddToggle(Main, {
    Name = "Rainbow Car",
    Default = false,
    Callback = function(Value)
        if Value then
            enableRainbowCar()
        else
            disableRainbowCar()
        end
    end
})

local args = {
    [1] = "Lights"
}

local carLightsEnabled = false
local carLightsLoop = nil

local function toggleCarLights()
    while carLightsEnabled do
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
        wait(0.5)
    end
end

local PhareVoitureBugToggle = AddToggle(Main, {
    Name = "Phare Voiture Bug",
    Default = false,
    Callback = function(Value)
        carLightsEnabled = Value
        if carLightsEnabled then
            carLightsLoop = coroutine.create(toggleCarLights)
            coroutine.resume(carLightsLoop)
        else
            if carLightsLoop then
                coroutine.yield(carLightsLoop)
            end
        end
    end
})

local args = {
    [1] = "WheelNumber"
}

local wheelNumberEnabled = false
local wheelNumberLoop = nil

local function toggleWheelNumber()
    while true do
        if wheelNumberEnabled then
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            wait(0.8)
        else
            break
        end
    end
end

local function stopWheelNumber()
    local args = {
        [1] = "WheelNumberStop"
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
end

local WheelNumberCheckbox = AddToggle(Main, {
    Name = "Défilement des numéros des roues",
    Default = false,
    Callback = function(Value)
        if Value then
            wheelNumberEnabled = true
            wheelNumberLoop = coroutine.create(toggleWheelNumber)
            coroutine.resume(wheelNumberLoop)
        else
            wheelNumberEnabled = false
            stopWheelNumber()
        end
    end
})

local vehicleHeightEnabled = false
local vehicleHeightLoop = nil

local function toggleVehicleHeight()
    while true do
        if vehicleHeightEnabled then
            local args = {
                [1] = "VehicleHeight",
                [2] = 1
            }
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            
            args[2] = 2
            wait(0.8)
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            
            args[2] = 3
            wait(0.8)
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            
            args[2] = 4
            wait(0.8)
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
        else
            break
        end
    end
en0
})

local changeCurtainsEnabled = false -- Variable indiquant si le changement de rideaux est activé ou non

local function changeCurtainsLoop()
    while changeCurtainsEnabled do
        local args = {
            [1] = "Curtains"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sHous1e"):FireServer(unpack(args))
         Toggle = AddToggle(Main, {
    Name = "Voler de la maison bug",
    Default = false,
    Callback = function(Value)
        changeCurtainsEnabled = Value
        if Value then
            changeCurtainsLoop()
        end
    end
})

local Toggle = AddToggle(Main, {
    Name = "Lavabos  Et Douche Maison activer/désactiver",
    Default = false,
    Callback = function(Value)
        if Value then
            local playerName = game.Players.LocalPlayer.Name
            local lavabos = {
                "WashHandsOn3" .. playerName,
                "WashHandsOn4" .. playerName,
                "ShowerOn" .. playerName,
                "WashHandsOn2" .. playerName,
                "ShowerOn2" .. playerName,
                "TubOn2" .. playerName,
                "TubOn" .. playerName,
                "WashHandsOn" .. playerName
            }
            for _, lavabo in ipairs(lavabos) do
                local args = {
                    [1] = lavabo
                }
                game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Animatio1nFir1eClien1t"):FireServer(unpack(args))
            end
          
        else
            local playerName = game.Players.LocalPlayer.Name
            local offActions = {
                "ShowerOff1",
                "ShowerOff2",
                "ShowerOff3",
                "ShowerOff4",
                "WashHandsOff1",
                "WashHandsOff2",
                "WashHandsOff3",
                "WashHandsOff4",
                "WashHandsOff5",
                "WashHandsOff6",
                "WashHandsOff",
                "ShowerOff",
            }
            for _, action in ipairs(offActions) do
                local args = {
                    [1] = action .. playerName
                }
                game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Animatio1nFir1eClien1t"):FireServer(unpack(args))
            end
           
        end
    end
})
                        
local section = AddSection(Main, {"Vehicule Transformation"})

AddButton(Main, {
    Name = "Transformation du véhicule",
    Callback = function()
        
        local argsMusiqueScooter = {
            [1] = "PickingScooterMusicText",
            [2] = "15689445424"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1NoMoto1rVehicle1s"):FireServer(unpack(argsMusiqueScooter))
        
        -- Jouer de la musique pour la transformation de la voiture
        local argsMusiqueVoiture = {
            [1] = "PickingCarMusicText",
            [2] = "15689445424"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(argsMusiqueVoiture))

        local actions = {
            { "Fire"},
            { "Smoke" },
            { "Duke" },
            { "200PlayerGiveSpeed", "100" },
            { "TurboStage", 1 },
            { "TurboStage", 2 },
            { "TurboStage", 3 },
            { "DriftingNumber", 1.1 },
            { "DriftingNumber", 1.2000000000000002 },
            { "DriftingNumber", 1.3000000000000003 },
            { "DriftingNumber", 1.4000000000000004 },
            { "DriftingNumber", 1.5000000000000004 }
        }
        
        for _, args in ipairs(actions) do
            local argDelay = args[1] == "TurboStage" and 0.1 or 0.3
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            wait(argDelay)
        end
    end
})

-- Rainbow Car
local RainbowCarEnabled = false
local RainbowCarColors = {
    Color3.new(0.048056721687316895, 0, 1),
    Color3.new(0.048056721687316895, 0, 1),
    Color3.new(0, 1, 0.9987940788269043),
    Color3.new(0, 1, 0.30482882261276245),
    Color3.new(0.8824552893638611, 1, 0),
    Color3.new(1, 0.37878429889678955, 0),
    Color3.new(1, 0, 0.07956933975219727),
    Color3.new(0.9731431007385254, 0, 1),
    Color3.new(0.40603363513946533, 0, 1),
    Color3.new(0, 0, 0)
}
local currentCarColorIndex = 1

local function changeCarColor(color)
    local args = {
        [1] = "PickingCarColor",
        [2] = color
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
end

local function enableRainbowCar()
    RainbowCarEnabled = true
    while RainbowCarEnabled do
        changeCarColor(RainbowCarColors[currentCarColorIndex])
        currentCarColorIndex = (currentCarColorIndex % #RainbowCarColors) + 1
        wait(1)
    end
end

local function disableRainbowCar()
    RainbowCarEnabled = false
    currentCarColorIndex = 1
end

local JoueurToggleRainbowCar = AddToggle(Main, {
    Name = "Rainbow Car",
    Default = false,
    Callback = function(Value)
        if Value then
            enableRainbowCar()
        else
            disableRainbowCar()
        end
    end
})

local args = {
    [1] = "Lights"
}

local carLightsEnabled = false
local carLightsLoop = nil

local function toggleCarLights()
    while carLightsEnabled do
        game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
        wait(0.5)
    end
end

local PhareVoitureBugToggle = AddToggle(Main, {
    Name = "Phare Voiture Bug",
    Default = false,
    Callback = function(Value)
        carLightsEnabled = Value
        if carLightsEnabled then
            carLightsLoop = coroutine.create(toggleCarLights)
            coroutine.resume(carLightsLoop)
        else
            if carLightsLoop then
                coroutine.yield(carLightsLoop)
            end
        end
    end
})

local args = {
    [1] = "WheelNumber"
}

local wheelNumberEnabled = false
local wheelNumberLoop = nil

local function toggleWheelNumber()
    while true do
        if wheelNumberEnabled then
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            wait(0.8)
        else
            break
        end
    end
end

local function stopWheelNumber()
    local args = {
        [1] = "WheelNumberStop"
    }
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
end

local WheelNumberCheckbox = AddToggle(Main, {
    Name = "Défilement des numéros des roues",
    Default = false,
    Callback = function(Value)
        if Value then
            wheelNumberEnabled = true
            wheelNumberLoop = coroutine.create(toggleWheelNumber)
            coroutine.resume(wheelNumberLoop)
        else
            wheelNumberEnabled = false
            stopWheelNumber()
        end
    end
})

local vehicleHeightEnabled = false
local vehicleHeightLoop = nil

local function toggleVehicleHeight()
    while true do
        if vehicleHeightEnabled then
            local args = {
                [1] = "VehicleHeight",
                [2] = 1
            }
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            
            args[2] = 2
            wait(0.8)
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            
            args[2] = 3
            wait(0.8)
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
            
            args[2] = 4
            wait(0.8)
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Player1sCa1r"):FireServer(unpack(args))
        else
            break
        end
    end
end

local VehicleHeightCheckbox = AddToggle(Main, {
    Name = "Modification de la Hauteur du Véhicule",
    Default = false,
    Callback = function(Value)
        if Value then
            vehicleHeightEnabled = true
            vehicleHeightLoop = coroutine.create(toggleVehicleHeight)
            coroutine.resume(vehicleHeightLoop)
        else
            vehicleHeightEnabled = false
        end
    end
})
