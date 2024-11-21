local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local lastHitTime = {} 

workspace.Thrown.ChildAdded:Connect(function(child)
	task.defer(function()
		if child.Name == "Clone_Rig" then
			if child:FindFirstChild("Shirt") then
				if child.Shirt.ShirtTemplate == game.Players.LocalPlayer.Character.Shirt.ShirtTemplate then
					child:Destroy()
				end
			end
		end
	end)
end)



local sigma = true
local rightleft = false
local httpservice = game:GetService("HttpService")

local http_request = syn and syn.request or http and http.request or http_request or request or httprequest

local suMessage = "Has Been Made!"

local function downloadSoundFile(sn, url)
	if not isfile(sn) then
		if url:find("https://cdn.discordapp.com/attachments/") then
			local response = request({Url = url, Method = "GET"}).Body
			writefile(sn, response)
			print("Downloaded: " .. sn .. " " .. suMessage)
		else
			error("Invalid URL")
		end
	end
	return getcustomasset(sn)
end

local KokusenFileName = "Kokusen.mp3"
local KokusenURL = "https://cdn.discordapp.com/attachments/1128036348591349973/1294577581625966662/Kokusen.mp3?ex=670b84d3&is=670a3353&hm=7a028bb581afb5b90d2f1ed6dcfb2c6fc73e56105586909c2e79d9ddbaaf2308&"
local Kokusen2FileName = "youtube-bgfznw-a0ms-audio_tfzS4wui (1)"
local Kokusen2URL = "https://cdn.discordapp.com/attachments/1293648959465853058/1295080954318028951/youtube-bgfznw-a0ms-audio_tfzS4wui_1.mp3?ex=670d59a0&is=670c0820&hm=4c524572a0d0efd37de0e049c2f470c86e6e461833fe8aded6ee5679645d86f3&"
local Kokusen3FileName = "videoplayback-1-online-video-cuttercom_FKCenFoR.mp3"
local Kokusen3URL = "https://cdn.discordapp.com/attachments/1293648959465853058/1295078795446845514/videoplayback-1-online-video-cuttercom_FKCenFoR.mp3?ex=670d579e&is=670c061e&hm=97ece26320818e6fb24b73c8e2fc3592449664448c56c8d15f8fe22b72f78f4a&"
local ScreamFileName = "Mahito's Terrifying Scream Shakes Itadori  Jujutsu Kaisen Ep 18 (mp3cut.net)"
local ScreamURL = "https://cdn.discordapp.com/attachments/1293648959465853058/1295085009748758568/Mahitos_Terrifying_Scream_Shakes_Itadori_Jujutsu_Kaisen_Ep_18_mp3cut.net.mp3?ex=671151e7&is=67100067&hm=6c26348fc37a2799328f67fc81082a43d218af8bc614ec297e396e5b9513eeda&"
local LaughFileName = "youtube_mQpGO2G5lAk_audio-[AudioTrimmer.com].mp3"
local LaughURL = "https://cdn.discordapp.com/attachments/1128036348591349973/1296506647627432067/youtube_mQpGO2G5lAk_audio-AudioTrimmer.com.mp3?ex=67128968&is=671137e8&hm=7acb9fba45242d9491f6718fcdebd1d89ac4410a9bfdf02c1c16d94923eeb9a9&"
local MusicFileName = "Jujutsu Kaisen OST S2 EP 17, malevolent shrine best part only.mp3"
local MusicURL = "https://cdn.discordapp.com/attachments/1128036348591349973/1296507044278571119/Jujutsu_Kaisen_OST_S2_EP_17_malevolent_shrine_best_part_only.mp3?ex=671289c7&is=67113847&hm=e4c5a1f213189512c73ac1ff2d7bb9ed2ebddcd5b8ce9cfabe0ea94d6c0d47ec&"
local LeftRightFileName = "Dumb Wit It (Tiktok Version) I'm right I'm left I'm right I'm reght (mp3cut.net).mp3"
local LeftRightURL = "https://cdn.discordapp.com/attachments/1293648959465853058/1297235607998697572/Dumb_Wit_It_Tiktok_Version_Im_right_Im_left_Im_right_Im_reght_mp3cut.net.mp3?ex=6715304e&is=6713dece&hm=14f4e5e30be9aee9127fb7dde53fea05afb0d6343428ce9920f1522ed4057b45&"

downloadSoundFile(KokusenFileName, KokusenURL)
downloadSoundFile(Kokusen2FileName, Kokusen2URL)
downloadSoundFile(Kokusen3FileName, Kokusen3URL)
downloadSoundFile(ScreamFileName, ScreamURL)
downloadSoundFile(LaughFileName, LaughURL)
downloadSoundFile(MusicFileName, MusicURL)
downloadSoundFile(LeftRightFileName, LeftRightURL)

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local LocalPlayer = Players.LocalPlayer
local ts = game:GetService("TweenService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local TextChatService = game:GetService("TextChatService")
local AnimationId = "rbxassetid://14056379526"
local soundid = "rbxassetid://6892830182"
local db = false
local ts = game:GetService("TweenService")


local animationReplacements = {
	["rbxassetid://12272894215"] = {"rbxassetid://13560306510", 1.2}, -- flowing startup
	["rbxassetid://12273188754"] = {"rbxassetid://18897695481", 1}, -- flowing hit 18897695481
	["rbxassetid://12296882427"] = {"rbxassetid://18897119503", 1.3}, -- whirlwind stream  startup 
	["rbxassetid://12296113986"] = {"rbxassetid://18464356233", 1}, -- whirlwind stream hit 
	--["rbxassetid://12307656616"] = {"rbxassetid://17838619895", 1.5}, -- hunters grasp startup
	--["rbxassetid://12309835105"] = {"rbxassetid://18896127525", 1.3}, -- hunters grasp
	["rbxassetid://10479335397"] = {"rbxassetid://13365849295", 1}, -- dash
	["rbxassetid://12463072679"] = {"rbxassetid://16139402582", 1}, -- final hunt



}
local function tweenProperty(object, properties, duration)
	local tweenInfo = TweenInfo.new(duration, Enum.EasingStyle.Cubic, Enum.EasingDirection.InOut)
	local tween = ts:Create(object, tweenInfo, properties)
	tween:Play()
end
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")
local animator = humanoid:FindFirstChildOfClass("Animator")



local function playsound(soundid, volume, parent)
	coroutine.wrap(function()

		local sound = Instance.new("Sound")
		sound.SoundId = "rbxassetid://"..soundid
		sound.Volume = volume
		sound.Parent = parent
		sound:Play()
		sound.Ended:Wait()
		sound:Destroy()
	end)()
end
local cleave = false
local canUse = true

local function isHunterplaying()
	for _, track in pairs(humanoid:GetPlayingAnimationTracks()) do
		if track.Animation.AnimationId == "rbxassetid://12309835105" then
			return true 
		end
	end
	return false 
end




local function resetHotbarText()
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar:WaitForChild("1").Base.ToolName.Text = "Divergent Combo"

	LocalPlayer.PlayerGui.ScreenGui:WaitForChild("MagicHealth").Health.Bar.Bar.ImageColor3 = Color3.fromRGB(171, 0, 0)
	LocalPlayer.PlayerGui.ScreenGui.MagicHealth.TextLabel.Text = "King of Curses"
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar:WaitForChild("1").Base.Reuse.Visible = true
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar:WaitForChild("3").Base.Reuse.Visible = true

	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["2"].Base.ToolName.Text = "Crushing Blow"
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["3"].Base.ToolName.Text = "Grasping Cleave"
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["4"].Base.ToolName.Text = "Manji Kick"
end


local function ultmoves()
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar:WaitForChild("1").Base.ToolName.Text = "Unforgiving Barrage"
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["2"].Base.ToolName.Text = "Demonic Charge"
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["3"].Base.ToolName.Text = "Cursed Punch"
	LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["4"].Base.ToolName.Text = "Rush"
end



local function onUltedChanged()
	local ulted = character:GetAttribute("Ulted")

	if ulted == false then
		coroutine.wrap(function()
			repeat wait() until LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar["1"].Base.ToolName.Text == "Flowing Water"
			resetHotbarText()
			game.Players.LocalPlayer.Character.Head:WaitForChild("MusicULT"):Destroy()
		end)()
	else
		repeat wait() until LocalPlayer.PlayerGui.Hotbar.Backpack.Hotbar:WaitForChild("2").Base.ToolName.Text == "The Final Hunt"
		ultmoves()
	end

end

character:GetAttributeChangedSignal("Ulted"):Connect(onUltedChanged)

local function setupAnimationReplacement(animator)
	local BufferTrack = nil

	local function onAnimationPlayed(animationTrack)
		local animationId = animationTrack.Animation.AnimationId
		
		if animationId == "rbxassetid://12467789963" then
			coroutine.wrap(function()
				task.wait(0.75)
				local music = Instance.new("Sound", game.Players.LocalPlayer.Character.Head)

				music.Name = "Kokusen"

				music.SoundId = getcustomasset(KokusenFileName)

				music.TimePosition = 0.2

				music.Looped = false

				music.Volume = 10

				music:Play()
				game.Debris:AddItem(music, 60)

				local music2 = Instance.new("Sound", game.Players.LocalPlayer.Character.Head)

				music2.Name = "Kokusen2"

				music2.SoundId = getcustomasset(Kokusen2FileName)

				music2.TimePosition = 0.2

				music2.Looped = false

				music2.Volume = 10

				music2:Play()
				game.Debris:AddItem(music2, 60)

				local music3 = Instance.new("Sound", game.Players.LocalPlayer.Character.Head)

				music3.Name = "Kokusen3"

				music3.SoundId = getcustomasset(Kokusen3FileName)

				music3.TimePosition = 0.2

				music3.Looped = false

				music3.Volume = 0

				music3:Play()
				tweenProperty(music3, {Volume = 5}, 1)
				game.Debris:AddItem(music3, 60)

				local BlackFlashHit = Instance.new("Part")
				game.Debris:AddItem(BlackFlashHit, 5)
				BlackFlashHit.CFrame = game.Players.LocalPlayer.Character["Right Arm"].CFrame
				local Sparks2 = Instance.new("ParticleEmitter")
				local Blast = Instance.new("ParticleEmitter")
				local Lightning = Instance.new("ParticleEmitter")
				local Wind2 = Instance.new("ParticleEmitter")
				local Sparks = Instance.new("ParticleEmitter")
				-- Properties --

				BlackFlashHit.Anchored = true
				BlackFlashHit.BottomSurface = Enum.SurfaceType.Smooth
				BlackFlashHit.CanCollide = false
				BlackFlashHit.EnableFluidForces = false
				BlackFlashHit.Size = Vector3.new(1, 1, 1)
				BlackFlashHit.TopSurface = Enum.SurfaceType.Smooth
				BlackFlashHit.Transparency = 1
				BlackFlashHit.Name = [[BlackFlashHit]]
				BlackFlashHit.Parent = workspace

				Sparks2.Acceleration = Vector3.new(0, 5, 0)
				Sparks2.Brightness = 15
				Sparks2.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(1,0,0),0),ColorSequenceKeypoint.new(1,Color3.new(1,0,0),0)})
				Sparks2.Drag = 7
				Sparks2.EmissionDirection = Enum.NormalId.Front
				Sparks2.Enabled = false
				Sparks2.FlipbookMode = Enum.ParticleFlipbookMode.OneShot
				Sparks2.Lifetime = NumberRange.new(1,2)
				Sparks2.Orientation = Enum.ParticleOrientation.VelocityParallel
				Sparks2.Rate = 400
				Sparks2:Emit(20)
				Sparks2.RotSpeed = NumberRange.new(-300,300)
				Sparks2.Rotation = NumberRange.new(0,360)
				Sparks2.Size = NumberSequence.new({NumberSequenceKeypoint.new(0,4,2),NumberSequenceKeypoint.new(1,0,0)})
				Sparks2.Speed = NumberRange.new(20,150)
				Sparks2.SpreadAngle = Vector2.new(360, 360)
				Sparks2.Texture = [[rbxassetid://17547405831]]
				Sparks2.Name = [[Sparks2]]
				Sparks2.Parent = BlackFlashHit

				Blast.Brightness = 10
				Blast.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(1,0,0),0),ColorSequenceKeypoint.new(1,Color3.new(1,0,0),0)})
				Blast.EmissionDirection = Enum.NormalId.Front
				Blast.Enabled = false
				Blast.Lifetime = NumberRange.new(0.05,0.05)
				Blast.Orientation = Enum.ParticleOrientation.VelocityParallel
				Blast.Rate = 200
				Blast:Emit(20)
				Blast.Rotation = NumberRange.new(-360,360)
				Blast.Size = NumberSequence.new({NumberSequenceKeypoint.new(0,10,0),NumberSequenceKeypoint.new(1,62.2016,0)})
				Blast.Speed = NumberRange.new(0.1,0.1)
				Blast.SpreadAngle = Vector2.new(360, 360)
				Blast.Squash = NumberSequence.new({NumberSequenceKeypoint.new(0,-3,0),NumberSequenceKeypoint.new(1,2.5125,0)})
				Blast.Texture = [[rbxassetid://7994629137]]
				Blast.Name = [[Blast]]
				Blast.Parent = BlackFlashHit

				Lightning.Brightness = 5
				Lightning.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(1,0,0),0),ColorSequenceKeypoint.new(1,Color3.new(1,0,0),0)})
				Lightning.Drag = 3
				Lightning.Enabled = false
				Lightning.FlipbookFramerate = NumberRange.new(20,40)
				Lightning.FlipbookLayout = Enum.ParticleFlipbookLayout.Grid4x4
				Lightning.FlipbookStartRandom = true
				Lightning.Lifetime = NumberRange.new(0.2,1.3)
				Lightning.LockedToPart = true
				Lightning.Orientation = Enum.ParticleOrientation.VelocityPerpendicular
				Lightning.Rate = 100
				Lightning:Emit(20)
				Lightning.Rotation = NumberRange.new(0,360)
				Lightning.Size = NumberSequence.new({NumberSequenceKeypoint.new(0,0,0),NumberSequenceKeypoint.new(0.033642,12.5435,11.3034),NumberSequenceKeypoint.new(0.075642,16.0988,11.5298),NumberSequenceKeypoint.new(0.109642,9.43785,12.5917),NumberSequenceKeypoint.new(0.177642,14.175,13.7364),NumberSequenceKeypoint.new(1,13.9192,13.4744)})
				Lightning.Speed = NumberRange.new(0.001,10)
				Lightning.SpreadAngle = Vector2.new(360, 360)
				Lightning.Texture = [[rbxassetid://14255829980]]
				Lightning.ZOffset = 2
				Lightning.Name = [[Lightning]]
				Lightning.Parent = BlackFlashHit

				Wind2.Brightness = 3
				Wind2.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(1,0,0),0),ColorSequenceKeypoint.new(1,Color3.new(1,0,0),0)})
				Wind2.Enabled = false
				Wind2.Lifetime = NumberRange.new(0.1,0.1)
				Wind2.LightEmission = 1
				Wind2.Orientation = Enum.ParticleOrientation.VelocityPerpendicular
				Wind2.Rate = 100
				Wind2:Emit(20)
				Wind2.Rotation = NumberRange.new(-360,360)
				Wind2.Size = NumberSequence.new({NumberSequenceKeypoint.new(0,80,0),NumberSequenceKeypoint.new(1,80,0)})
				Wind2.Speed = NumberRange.new(0.01,0.01)
				Wind2.SpreadAngle = Vector2.new(360, 360)
				Wind2.Squash = NumberSequence.new({NumberSequenceKeypoint.new(0,-3,0),NumberSequenceKeypoint.new(1,0,0)})
				Wind2.Texture = [[rbxassetid://1053548563]]
				Wind2.Transparency = NumberSequence.new({NumberSequenceKeypoint.new(0,0,0),NumberSequenceKeypoint.new(1,1,0)})
				Wind2.Name = [[Wind2]]
				Wind2.Parent = BlackFlashHit

				Sparks.Brightness = 15
				Sparks.Color = ColorSequence.new({ColorSequenceKeypoint.new(0,Color3.new(1,0,0),0),ColorSequenceKeypoint.new(1,Color3.new(1,0,0),0)})
				Sparks.Drag = 7
				Sparks.EmissionDirection = Enum.NormalId.Front
				Sparks.Enabled = false
				Sparks.Lifetime = NumberRange.new(0.8,1.3)
				Sparks.Orientation = Enum.ParticleOrientation.VelocityParallel
				Sparks.Rate = 400
				Sparks:Emit(20)
				Sparks.Rotation = NumberRange.new(90,90)
				Sparks.Size = NumberSequence.new({NumberSequenceKeypoint.new(0,4.02858,3.04993),NumberSequenceKeypoint.new(0.205642,1.84193,1.74011),NumberSequenceKeypoint.new(1,0,0)})
				Sparks.Speed = NumberRange.new(40,200)
				Sparks.SpreadAngle = Vector2.new(360, 360)
				Sparks.Squash = NumberSequence.new({NumberSequenceKeypoint.new(0,0,0),NumberSequenceKeypoint.new(0.231642,5.1956,0),NumberSequenceKeypoint.new(0.32206,0.844828,0),NumberSequenceKeypoint.new(0.46806,4.5586,0),NumberSequenceKeypoint.new(0.49206,0.000789245,0),NumberSequenceKeypoint.new(0.51806,3.78691,0),NumberSequenceKeypoint.new(0.56206,1.97825,0),NumberSequenceKeypoint.new(0.64006,2.28498,0),NumberSequenceKeypoint.new(0.72006,0.104659,0),NumberSequenceKeypoint.new(1,-1.15485,0)})
				Sparks.Texture = [[rbxassetid://15407518755]]
				Sparks.Name = [[Sparks]]
				Sparks.Parent = BlackFlashHit
				coroutine.wrap(function()


					local ts = game:GetService("TweenService")
					local Dialogue = Instance.new("BillboardGui")
					local Chat1 = Instance.new("Frame")
					local Sub = Instance.new("TextLabel")



					local player = game.Players.LocalPlayer
					local character = player.Character or player.CharacterAdded:Wait()
					local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

					Dialogue.Active = true
					Dialogue.Size = UDim2.new(15, 0, 15, 0)
					Dialogue.StudsOffset = Vector3.new(0, 0, 2)
					Dialogue.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
					Dialogue.Name = [[Dialogue]]
					Dialogue.Parent = humanoidRootPart

					Chat1.AnchorPoint = Vector2.new(0.5, 0.5)
					Chat1.BackgroundColor3 = Color3.new(1, 1, 1)
					Chat1.BorderColor3 = Color3.new(0, 0, 0)
					Chat1.BorderSizePixel = 2
					Chat1.Position = UDim2.new(0.600000024, 0, -0.2, 0) 
					Chat1.Size = UDim2.new(0.100000001, 0, 0.200000003, 0)
					Chat1.Name = [[Chat1]]
					Chat1.BackgroundTransparency = 1
					Chat1.Parent = Dialogue

					Sub.FontFace = Font.new("rbxassetid://12187375716", Enum.FontWeight.Bold, Enum.FontStyle.Italic)
					Sub.Text = [[KOKUSEN!!]]
					Sub.TextColor3 = Color3.new(0, 0, 0)
					Sub.TextScaled = true
					Sub.TextSize = 14
					Sub.TextWrapped = true
					Sub.AnchorPoint = Vector2.new(0.5, 0.5)
					Sub.BackgroundColor3 = Color3.new(1, 1, 1)
					Sub.TextTransparency = 1
					Sub.BorderColor3 = Color3.new(0, 0, 0)
					Sub.BorderSizePixel = 0
					Sub.Position = UDim2.new(0.5, 0, 0.5, 0)
					Sub.Size = UDim2.new(0.850000024, 0, 0.349999994, 0)
					Sub.Name = [[Sub]]
					Sub.Parent = Chat1
					Sub.BackgroundTransparency = 1






					game.Debris:AddItem(Chat1, 25)
					game.Debris:AddItem(Sub, 25)



					tweenProperty(Chat1, {BackgroundTransparency = 0}, 1)
					tweenProperty(Sub, {TextTransparency = 0}, 1)
					tweenProperty(Chat1, {Position = UDim2.new(0.6, 0, 0.4, 0)}, 1)
					task.wait(2)
					tweenProperty(Chat1, {BackgroundTransparency = 1}, 2)
					tweenProperty(Sub, {TextTransparency = 1}, 2)

				end)()
			end)()
		end
		

		if animationId == "rbxassetid://12342141464" then
			
			animationTrack:Stop()
			local c = Instance.new("Animation")
			c.AnimationId = "rbxassetid://15507137974"

			local emote = game.Players.LocalPlayer.Character.Humanoid:LoadAnimation(c)
			emote:Play()
			emote:AdjustSpeed(1.1)
			
			
			coroutine.wrap(function()
				repeat wait() until game.Players.LocalPlayer.Character.Head:FindFirstChild("MainWind")
				task.wait(0.1)
				local function changeToBlue(instance)
					if instance:IsA("ParticleEmitter") then
						instance.Color = ColorSequence.new(Color3.fromRGB(255, 0, 0))
					end
					if instance:IsA("Beam") then
						instance.Color = ColorSequence.new(Color3.fromRGB(255, 78, 78)) 
					end
				end

				for _, descendant in pairs(character:GetDescendants()) do
					changeToBlue(descendant)
				end
			end)()
			
			
			coroutine.wrap(function()
			local Players = game:GetService("Players")
			local Debris = game:GetService("Debris")
			local TweenService = game:GetService("TweenService")
			local RunService = game:GetService("RunService")

			local assetId = "rbxassetid://84715104558111"
			local objects = game:GetObjects(assetId)

			if #objects > 0 then
				local loadedObject = objects[1] 
				loadedObject.Parent = workspace

				local mainPart = loadedObject:FindFirstChild("Main")

				if mainPart then
					local hrp = character:WaitForChild("HumanoidRootPart")

					local behindPosition = hrp.CFrame * CFrame.new(0, -75, 30)
					mainPart.CFrame = behindPosition

					local tweenInfo = TweenInfo.new(3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
					local goalCFrame = behindPosition * CFrame.new(0, 73, 0) 
					tweenProperty(game.Lighting, {ClockTime = 0}, 2)
					local tween = TweenService:Create(mainPart, tweenInfo, { CFrame = goalCFrame })
					tween:Play()

					local camera = workspace.CurrentCamera
					local shakeIntensity = 1
					local shakeDuration = 3
					local elapsedTime = 0

					local connection
					connection = RunService.RenderStepped:Connect(function(deltaTime)
						if elapsedTime < shakeDuration then
							elapsedTime = elapsedTime + deltaTime
							local shakeOffset = Vector3.new(
								math.random(-shakeIntensity, shakeIntensity) * 0.1,
								math.random(-shakeIntensity, shakeIntensity) * 0.1,
								math.random(-shakeIntensity, shakeIntensity) * 0.1
							)
							camera.CFrame = camera.CFrame * CFrame.new(shakeOffset)
						else
							connection:Disconnect()
						end
					end)

						Debris:AddItem(loadedObject, 10)
						coroutine.wrap(function()
							task.wait(10)
							tweenProperty(game.Lighting, {ClockTime = 13.2}, 8)
						end)()
				end
				end
				end)()


			local music2 = Instance.new("Sound", game.Players.LocalPlayer.Character.Head)

			music2.Name = "Laugh"

			music2.SoundId =
