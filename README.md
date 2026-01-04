local p=game.Players.LocalPlayer local c=p.Character or p.CharacterAdded:Wait() local h=c:WaitForChild("Humanoid") local r=c:WaitForChild("HumanoidRootPart") local AF=false local ESP=false local g=Instance.new("ScreenGui",p.PlayerGui) g.Name="MobileHub"
local f=Instance.new("Frame",g) f.Size=UDim2.new(0,200,0,220) f.Position=UDim2.new(0.05,0,0.3,0) f.BackgroundColor3=Color3.fromRGB(20,20,20) f.Active=true f.Draggable=true
local function B(t,y) local b=Instance.new("TextButton",f) b.Size=UDim2.new(1,-20,0,45) b.Position=UDim2.new(0,10,0,y) b.Text=t b.TextScaled=true b.BackgroundColor3=Color3.fromRGB(45,45,45) b.TextColor3=Color3.new(1,1,1) return b end
local fb=B("AUTO FARM",10) local tb=B("TELEPORT",65) local eb=B("ESP",120) local sb=B("SPEED",175)
task.spawn(function() while task.wait(1) do if AF then for _,n in pairs(workspace.Enemies:GetChildren()) do if n:FindFirstChild("HumanoidRootPart") and n:FindFirstChild("Humanoid") and n.Humanoid.Health>0 then r.CFrame=n.HumanoidRootPart.CFrame*CFrame.new(0,0,3) break end end end end end)
fb.MouseButton1Click:Connect(function() AF=not AF fb.Text=AF and "AUTO FARM ON" or "AUTO FARM" end)
tb.MouseButton1Click:Connect(function() r.CFrame=CFrame.new(1100,15,-1500) end)
local function ESP_ON() for _,v in pairs(workspace:GetChildren()) do if v:FindFirstChild("Head") and v:FindFirstChild("Humanoid") and not v.Head:FindFirstChild("E") then local e=Instance.new("BillboardGui",v.Head) e.Name="E" e.Size=UDim2.new(0,90,0,35) e.AlwaysOnTop=true local t=Instance.new("TextLabel",e) t.Size=UDim2.new(1,0,1,0) t.BackgroundTransparency=1 t.Text=v.Name t.TextScaled=true t.TextColor3=Color3.new(1,0,0) end end end
local function ESP_OFF() for _,v in pairs(workspace:GetDescendants()) do if v:IsA("BillboardGui") and v.Name=="E" then v:Destroy() end end end
eb.MouseButton1Click:Connect(function() ESP=not ESP eb.Text=ESP and "ESP ON" or "ESP" if ESP then ESP_ON() else ESP_OFF() end end)
sb.MouseButton1Click:Connect(function() h.WalkSpeed=45 end)
