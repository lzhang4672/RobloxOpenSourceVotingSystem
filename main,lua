-- requires
local player = game:GetService('Players').LocalPlayer:WaitForChild('PlayerGui')
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local VoteCommunications = ReplicatedStorage:FindFirstChild("VoteCommunications")
local votevent = VoteCommunications:FindFirstChild("VoteEvent")
local voterefresh = VoteCommunications:FindFirstChild("RefreshVotes")
local refreshresult = VoteCommunications:FindFirstChild("ResultString")
local player = game:GetService('Players').LocalPlayer:WaitForChild('PlayerGui')
local vote = player:WaitForChild("VotingDiag").MainFrame

-- functions
TweenService = game:GetService("TweenService")

local function starttimer(tim)
	-- constants
	local timer = vote.Time
	timer.Text = tim
	for i = timer.Text, 0, -1 do
		if i <= 5 then
			timer.TextColor3 = Color3.fromRGB(255, 111, 105)
		end
		timer.Text = i
		wait(1)
	end
end

local function enable()
	vote:TweenPosition(UDim2.new(0.263, 0,0.46, 0))
	vote.Active = true
end

local function disable()
	vote:TweenPosition(UDim2.new(0.263, 0,1, 0))
	vote.Active = false
end

local function setup(option1, option2, tim)
	-- constants
	local optionA = vote.Selectionone
	local optionB = vote.Selectiontwo
	local optionAenabled = vote.Selectionone.LocalScript
	for i = 1, #option1 do
		local d = option1:sub(1, i)
		optionA.Text = d
	end
	for i = 1, #option2 do
		local d = option2:sub(1, i)
		optionB.Text = d
	end
	optionAenabled.Disabled = false
	starttimer(tim)
end


votevent.OnClientEvent:Connect(function(typ, option1, option2, tim)
	if typ == "EnableDiag" then
		enable()
	end
	if typ == "DisableDiag" then
		disable()
	end
	if typ == "starttimer" then
		starttimer(tim)
	end
	if typ == "setup" then
		setup(option1, option2, tim)
	end
end)


refreshresult.OnClientEvent:Connect(function(result)
	if result ~= nil then
		vote.OptionSelection:TweenPosition(UDim2.new(0.369, 0,0.203, 0), "Out", "Quad", 0.2, true)
		vote.OptionSelection.Position = UDim2.new(0.369, 0,0.203, 0)
		vote.OptionSelection.Selected.TextTransparency = 0
		vote.OptionSelection.Selected.TextColor3 = Color3.fromRGB(212, 238, 255)
		vote.OptionSelection.Selected.Text = result
		for i = 2, 0, -.1 do
			vote.OptionSelection.Selected.TextTransparency = i
		end
	end
end)


voterefresh.OnClientEvent:Connect(function(number, typ)
	local counterA = vote.Option1Count 
	local counterB = vote.Option2Count
	if typ == 'A' then
		counterA.Text = number
	end
	if typ == 'B' then
		counterB.Text = number
	end
	
	
end)

