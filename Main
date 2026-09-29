local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local localPlayer = Players.LocalPlayer
local playerGui = localPlayer:WaitForChild("PlayerGui")

local doorsAdmin = playerGui:WaitForChild("DoorsAdmin")
local entitiesPage = doorsAdmin:WaitForChild("Container"):WaitForChild("Pages"):WaitForChild("ENTITIES")
local contentsFolder = entitiesPage:WaitForChild("Entities"):WaitForChild("Spawn Entities"):WaitForChild("Contents")
local originalJack = contentsFolder:WaitForChild("Jack")
local adminRemote = ReplicatedStorage:WaitForChild("RemotesFolder"):WaitForChild("AdminPanelRunCommand")

local customEntities = {
	{ remoteName = "Teller",    displayText = "Teller" },
	{ remoteName = "Stem",      displayText = "Stem" },
	{ remoteName = "Bash",      displayText = "Bash" },
	{ remoteName = "Scribbles", displayText = "Scribbles" },
	{ remoteName = "Honcho",    displayText = "Honcho (not working for now)" },
	{ remoteName = "Alma",      displayText = "Alma (not working for now)" },
	{ remoteName = "Drones",    displayText = "Drones (not working for now)" },
	{ remoteName = "Noise",     displayText = "Noise (not working for now)" },
	{ remoteName = "Creak",     displayText = "Creak (not working for now)" },
}

for _, entity in ipairs(customEntities) do
	local newButton = originalJack:Clone()
	newButton.Name = entity.remoteName
	newButton.Parent = contentsFolder

	local titleLabel = newButton:WaitForChild("Container"):WaitForChild("Title")
	if titleLabel:IsA("TextLabel") or titleLabel:IsA("TextButton") then
		titleLabel.Text = entity.displayText
	end

	local clickTarget = newButton:IsA("GuiButton") and newButton or newButton:FindFirstChildWhichIsA("GuiButton", true)
	if clickTarget then
		clickTarget.MouseButton1Click:Connect(function()
			adminRemote:FireServer(entity.remoteName, {})
		end)
	end
end
