-- ===============================
-- RGB HUB | RAYFIELD CAMERA HUB
-- ===============================

local Rayfield = loadstring(game:HttpGet("https://sirius.menu/rayfield"))()

local Window = Rayfield:CreateWindow({
	Name = "RGB HUB",
	LoadingTitle = "RGB HUB",
	LoadingSubtitle = "Free Camera",
	ConfigurationSaving = {
		Enabled = false
	}
})

Rayfield:Notify({
	Title = "RGB HUB",
	Content = "SCRIPT FREE  CÂMERA ON 📷",
	Duration = 5
})

-- ===============================
-- TAB
-- ===============================
local Tab = Window:CreateTab("📷 CÂMERA", 4483362458)

-- ======================================================
-- 📱 MOBILE CAMERA (COM TOOL - NÃO ATIVA SOZINHO)
-- ======================================================
Tab:CreateButton({
	Name = "📱 Mobile Câmera",
	Callback = function()
		loadstring([[
local P,R,U,W=game:GetService("Players"),game:GetService("RunService"),game:GetService("UserInputService"),game:GetService("Workspace")
local p,c=P.LocalPlayer,W.CurrentCamera
local PM=require(p:WaitForChild("PlayerScripts"):WaitForChild("PlayerModule"))
local C=PM:GetControls()

-- EVITA TOOL DUPLICADO
if p.Backpack:FindFirstChild("🎥 Cam") then return end

local t=Instance.new("Tool")
t.Name="🎥"
t.RequiresHandle=false
t.CanBeDropped=false
t.Parent=p.Backpack

local MS,SF,SX,SY=60,12,0.006,0.004
local en,ci=false,nil
local tx,ty,cx,cy=0,0,0,0

local cn,ca,rd,cl=CFrame.new,CFrame.fromEulerAnglesYXZ,math.rad,math.clamp

local function ec()
	en=true
	if p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
		p.Character.HumanoidRootPart.Anchored=true
	end
	c.CameraType=Enum.CameraType.Scriptable
	local x,y=c.CFrame:ToEulerAnglesYXZ()
	tx,ty,cx,cy=x,y,x,y
	R:BindToRenderStep("FCM",201,function(dt)
		if not en then return end
		local a=1-math.exp(-SF*dt)
		cx=cx+(tx-cx)*a
		cy=cy+(ty-cy)*a
		local rcf=ca(cx,cy,0)
		local iv=C:GetMoveVector()
		if iv.Magnitude>0 then
			local md=(rcf.LookVector*-iv.Z)+(rcf.RightVector*iv.X)
			c.CFrame=cn(c.CFrame.Position+(md*MS*dt))*rcf
		else
			c.CFrame=cn(c.CFrame.Position)*rcf
		end
	end)
end

local function dc()
	en=false
	pcall(function() R:UnbindFromRenderStep("FCM") end)
	if ci then ci:Disconnect() ci=nil end
	if p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
		p.Character.HumanoidRootPart.Anchored=false
	end
	c.CameraType=Enum.CameraType.Custom
	if p.Character and p.Character:FindFirstChild("Humanoid") then
		c.CameraSubject=p.Character.Humanoid
	end
end

t.Equipped:Connect(function()
	task.spawn(function()
		pcall(function() C=PM:GetControls() end)
	end)
	ec()
	ci=U.InputChanged:Connect(function(i)
		if not en then return end
		if i.UserInputType==Enum.UserInputType.Touch
		or i.UserInputType==Enum.UserInputType.MouseMovement then
			local d=i.Delta
			ty=ty-(d.X*SX)
			tx=tx-(d.Y*SY)
			tx=cl(tx,rd(-89),rd(89))
		end
	end)
end)

t.Unequipped:Connect(dc)
]])()
	end
})

-- ======================================================
-- 🖥️ PC CAMERA (TECLA K)
-- ======================================================
Tab:CreateToggle({
	Name = "🖥️ PC Câmera (Tecla K)",
	CurrentValue = false,
	Callback = function(Value)
		if Value then
			loadstring([[
local P,R,U,W=game:GetService("Players"),game:GetService("RunService"),game:GetService("UserInputService"),game:GetService("Workspace")
local p,c=P.LocalPlayer,W.CurrentCamera
local PM=require(p:WaitForChild("PlayerScripts"):WaitForChild("PlayerModule"))
local C=PM:GetControls()

local MS,SF,SX,SY=60,12,0.006,0.004
local en,ci=false,nil
local tx,ty,cx,cy=0,0,0,0

local cn,ca,rd,cl=CFrame.new,CFrame.fromEulerAnglesYXZ,math.rad,math.clamp

local function ec()
	en=true
	if p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
		p.Character.HumanoidRootPart.Anchored=true
	end
	c.CameraType=Enum.CameraType.Scriptable
	local x,y=c.CFrame:ToEulerAnglesYXZ()
	tx,ty,cx,cy=x,y,x,y
	R:BindToRenderStep("FCM",201,function(dt)
		if not en then return end
		local a=1-math.exp(-SF*dt)
		cx=cx+(tx-cx)*a
		cy=cy+(ty-cy)*a
		local rcf=ca(cx,cy,0)
		local iv=C:GetMoveVector()
		if iv.Magnitude>0 then
			local md=(rcf.LookVector*-iv.Z)+(rcf.RightVector*iv.X)
			c.CFrame=cn(c.CFrame.Position+(md*MS*dt))*rcf
		else
			c.CFrame=cn(c.CFrame.Position)*rcf
		end
	end)
end

local function dc()
	en=false
	pcall(function() R:UnbindFromRenderStep("FCM") end)
	if ci then ci:Disconnect() ci=nil end
	if p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
		p.Character.HumanoidRootPart.Anchored=false
	end
	c.CameraType=Enum.CameraType.Custom
	if p.Character and p.Character:FindFirstChild("Humanoid") then
		c.CameraSubject=p.Character.Humanoid
	end
end

ci=U.InputChanged:Connect(function(i)
	if not en then return end
	if i.UserInputType==Enum.UserInputType.MouseMovement then
		local d=i.Delta
		ty=ty-(d.X*SX)
		tx=cl(tx-(d.Y*SY),rd(-89),rd(89))
	end
end)

U.InputBegan:Connect(function(i,gp)
	if gp then return end
	if i.KeyCode==Enum.KeyCode.K then
		if en then dc() else ec() end
	end
end)
]])()
		end
	end
})
