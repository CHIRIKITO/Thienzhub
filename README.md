if napoleonLoaded then
    return
end

pcall(function()
    getgenv().napoleonLoaded = true
end)

local api = loadstring(
    game:HttpGet('https://sdkapi-public.luarmor.net/library.lua')
)()

local TeleportService: TeleportService = cloneref(game:GetService("TeleportService"))

local repo = 'https://raw.githubusercontent.com/raydjs/Obsidian/main/'
local discord_link = 'discord.gg/bWzCFPk83g'
local Library = nil

while true do task.wait()
	local success, data = pcall(function()
		return loadstring(game:HttpGet(repo .. 'Library.lua'))()
	end)

	if success then
		Library = data
		break
	end
end

local ID = game.GameId

local games = if ID == 6931042565 then
   	if old then '5138fff8319f430c56ea6057569cb188' else '10231c45388ada5c77add5a7583a2b19'
    elseif ID == 7018190066 then
	    '6cb8843504e7bbaf2c12ad7fe51d8e60'
	elseif ID == 6945584306 then
	    'd48f6f73e12d8c126f3075f73224ea83'
	elseif ID == 1054526971 then
		'2e637d8f45504b786dccd6c6478e468f'
	else
        nil

if games == nil then
	return
end
       
api.script_id = games

-- Bỏ kiểm tra key và chạy script luôn
Library:Unload()
Library:Notify("Thienz Hub loaded (key bypassed)", 4)
api.load_script()

-- Optional GUI with Thienz name
local Window = Library:CreateWindow({
	Title = "Thienz Hub",
	Footer = discord_link,
	Icon = 105747086514734,
	NotifySide = "Right",
	ShowCustomCursor = false,
    MobileButtonsSide = "Left",
})

local Tabs = {
    Main = Window:AddTab("Main"),
}

Tabs.Main:AddButton({
    Text = "Join Discord",
    Func = function()
        setclipboard(discord_link)
        Library:Notify("Discord Link copied", 4)
    end,
})

Tabs.Main:AddButton({
    Text = "Rejoin Server",
    Func = function()
        TeleportService:Teleport(game.PlaceId)
        Library:Notify("Rejoining ...", 4)
    end,
})
