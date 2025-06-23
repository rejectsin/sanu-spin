-- 🏐 Volleyball Legends - Sterling Hub Lite: Auto Sanu + Hitbox + Farm

local plr = game.Players.LocalPlayer
local rs = game:GetService("ReplicatedStorage")
local vim = game:GetService("VirtualInputManager")
local autoSpin = false
local autoFarm = false
local targetStyle = "Sanu"

-- 🔔 Notification
function notify(msg)
    game.StarterGui:SetCore("SendNotification", {
        Title = "Sterling Hub",
        Text = msg,
        Duration = 5
    })
end

-- 🎰 Auto Spin Until SANU
function startAutoSpin()
    coroutine.wrap(function()
        while autoSpin do
            local gui = plr.PlayerGui:FindFirstChild("Interface")
            if gui and gui:FindFirstChild("Lobby") then
                local styleName = gui.Lobby.Styles.TopPanel.DisplayName.Text
                if styleName == targetStyle then
                    autoSpin = false
                    notify("🎯 You got SANU!")
                    break
                else
                    rs.Packages._Index["sleitnick_knit@1.7.0"].knit.Services.StylesService.RF.Roll:InvokeServer(false)
                    wait(0.4)
                end
            end
            wait(0.4)
        end
    end)()
end

-- ⚙️ Hitbox Expander
function expandHitboxes(size)
    local hitboxes = rs:WaitForChild("Assets"):WaitForChild("Hitboxes")
    for _, folder in pairs(hitboxes:GetChildren()) do
        if folder:FindFirstChild("Part") then
            folder.Part.Size = Vector3.new(size, size, size)
        end
    end
    notify("📦 Hitboxes expanded to size " .. size)
end

-- 🔁 Auto Farm Basic
function startAutoFarm()
    coroutine.wrap(function()
        while autoFarm do
            local ball = nil
            for _, model in pairs(workspace:GetChildren()) do
                if model:IsA("Model") and model.Name:match("CLIENT_BALL_") then
                    ball = model:FindFirstChild("Sphere.001") or model:FindFirstChild("Cube.001")
                end
            end
            if ball then
                plr.Character:MoveTo(ball.Position)
            end
            wait(1.5)
        end
    end)()
end

-- 🟢 STARTUP
notify("Sterling Hub Loaded.\nAuto Farm ON\nAuto Spin ON\nHitbox 50")

autoFarm = true
autoSpin = true

expandHitboxes(50)
startAutoFarm()
startAutoSpin()
