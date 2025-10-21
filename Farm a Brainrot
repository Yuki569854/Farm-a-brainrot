--[[ 
🧠 Farm a Brainrot | Rayfield GUI (2 Tabs)
💬 Subtitle: YUKKOTSU
]]

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
	Name = "Farm a Brainrot | YUKKOTSU",
	LoadingTitle = "Farm a Brainrot",
	LoadingSubtitle = "by YUKKOTSU",
	ConfigurationSaving = {
		Enabled = true,
		FolderName = "FarmABrainrot",
		FileName = "YUKKOTSU_Config"
	},
	KeySystem = false
})

-- ⚙️ Services
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Functions = ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("Functions")

-- 🪣 Cans Tab
local CansTab = Window:CreateTab("Cans", 4483362458)
-- 🧠 Brainrot Tab
local BrainrotTab = Window:CreateTab("Brainrot", 4483362458)

-- Lists
local CanList = {"Water Can", "Gold Water Can", "Diamond Water Can", "Rainbow Water Can"}
local BrainrotList = {
	"Tralalero Tralala",
	"La Vaca Saturno Saturnita",
	"Matteo",
	"Pot Hotspot",
	"Garama and Madundung",
	"La Grande Combinasion",
	"Los Tralaleritos",
	"Esok Sekolah",
	"KarKerKar KurKur",
	"Ketchuru and Musturu",
	"Smurf Cat",
	"Spaghetti Tualetti"
}

-- Functions
local function BuyCan(name)
	pcall(function()
		Functions:WaitForChild("CheckBoughtCan"):InvokeServer(name)
	end)
end

local function BuyBrainrot(name)
	pcall(function()
		Functions:WaitForChild("CheckBought"):InvokeServer(name)
	end)
end

-- Active toggles
local ActiveToggles = {
	Cans = {},
	Brainrot = {}
}

-------------------------------------------------
-- 🪣 Cans Tab Toggles
-------------------------------------------------
local CansSection = CansTab:CreateSection("🪣 AutoBuy Cans")

for _, name in ipairs(CanList) do
	CansTab:CreateToggle({
		Name = "Auto Buy " .. name,
		CurrentValue = false,
		Callback = function(value)
			ActiveToggles.Cans[name] = value
			if value then
				task.spawn(function()
					while ActiveToggles.Cans[name] do
						BuyCan(name)
						task.wait(2)
					end
				end)
			end
		end
	})
end

CansTab:CreateButton({
	Name = "🛑 Stop All Cans",
	Callback = function()
		for k in pairs(ActiveToggles.Cans) do
			ActiveToggles.Cans[k] = false
		end
		Rayfield:Notify({
			Title = "AutoBuy Cans",
			Content = "⛔ All Can auto-buys stopped.",
			Duration = 3
		})
	end
})

-------------------------------------------------
-- 🧠 Brainrot Tab Toggles
-------------------------------------------------
local BrainrotSection = BrainrotTab:CreateSection("🧠 AutoBuy Brainrots")

for _, name in ipairs(BrainrotList) do
	BrainrotTab:CreateToggle({
		Name = "Auto Buy " .. name,
		CurrentValue = false,
		Callback = function(value)
			ActiveToggles.Brainrot[name] = value
			if value then
				task.spawn(function()
					while ActiveToggles.Brainrot[name] do
						BuyBrainrot(name)
						task.wait(2)
					end
				end)
			end
		end
	})
end

BrainrotTab:CreateButton({
	Name = "🛑 Stop All Brainrots",
	Callback = function()
		for k in pairs(ActiveToggles.Brainrot) do
			ActiveToggles.Brainrot[k] = false
		end
		Rayfield:Notify({
			Title = "AutoBuy Brainrots",
			Content = "⛔ All Brainrot auto-buys stopped.",
			Duration = 3
		})
	end
})

-------------------------------------------------
-- ✅ Final Notify
-------------------------------------------------
Rayfield:Notify({
	Title = "Farm a Brainrot | YUKKOTSU",
	Content = "✅ GUI Loaded Successfully with Two Tabs!",
	Duration = 4
})
