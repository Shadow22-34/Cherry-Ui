# 🍒 Cherry Hub UI Library

<div align="center">
  <img src="assets/cherry-logo.png" alt="Cherry Hub Logo" width="200">
  <br>
  <h3>A sleek, modern UI library for Roblox exploits</h3>
  <br>
</div>

## 📋 Features

- **Elegant Design**: Smooth animations and modern aesthetics
- **Easy to Use**: Simple API for creating beautiful interfaces
- **Customizable**: Adapt the UI to match your script's style
- **Lightweight**: Optimized for performance
- **Cross-Exploit Compatible**: Works with most popular Roblox executors

## 🚀 Getting Started

### Installation

```lua
local CherryHub = {}
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")

-- USERS  DO NOT TOUCH THIS!
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Shadow = Instance.new("ImageLabel")
local TopBar = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Logo = Instance.new("ImageLabel")
local CloseButton = Instance.new("ImageButton")
local MinimizeButton = Instance.new("ImageButton")
local TabContainer = Instance.new("Frame")
local ContentContainer = Instance.new("Frame")

-- UI Properties
ScreenGui.Name = "ENTER HERE"
ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.ResetOnSpawn = false

-- USERS  DO NOT TOUCH THIS!
Shadow.Name = "Shadow"
Shadow.Parent = ScreenGui
Shadow.AnchorPoint = Vector2.new(0.5, 0.5)
Shadow.BackgroundTransparency = 1
Shadow.Position = UDim2.new(0.5, 0, 0.5, 0)
Shadow.Size = UDim2.new(0, 620, 0, 420)
Shadow.Image = "rbxassetid://6015897843"
Shadow.ImageColor3 = Color3.fromRGB(0, 0, 0)
Shadow.ImageTransparency = 0.6
Shadow.ScaleType = Enum.ScaleType.Slice
Shadow.SliceCenter = Rect.new(49, 49, 450, 450)

-- USERS  DO NOT TOUCH THIS!
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.AnchorPoint = Vector2.new(0.5, 0.5)
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 20) -- Base dark color
MainFrame.BorderSizePixel = 0
MainFrame.Position = UDim2.new(0.5, 0, 0.5, 0)
MainFrame.Size = UDim2.new(0, 600, 0, 400)
MainFrame.ClipsDescendants = true

-- USERS  DO NOT TOUCH THIS!
local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 10)
UICorner.Parent = MainFrame

-- USERS  DO NOT TOUCH THIS!
TopBar.Name = "TopBar"
TopBar.Parent = MainFrame
TopBar.BackgroundColor3 = Color3.fromRGB(15, 15, 20) -- Match main frame color
TopBar.BorderSizePixel = 0
TopBar.Size = UDim2.new(1, 0, 0, 40)

local TopBarCorner = Instance.new("UICorner")
TopBarCorner.CornerRadius = UDim.new(0, 10)
TopBarCorner.Parent = TopBar

-- Cherry Hub Logo
Logo.Name = "Logo"
Logo.Parent = TopBar
Logo.BackgroundTransparency = 1
Logo.Position = UDim2.new(0, 10, 0.5, -12)
Logo.Size = UDim2.new(0, 24, 0, 24)
Logo.Image = "rbxassetid://6031302931" -- Cherry icon
Logo.ImageColor3 = Color3.fromRGB(255, 80, 100)

-- Title
Title.Name = "Title"
Title.Parent = TopBar
Title.BackgroundTransparency = 1
Title.Position = UDim2.new(0, 44, 0, 0)
Title.Size = UDim2.new(0, 200, 1, 0)
Title.Font = Enum.Font.GothamBold
Title.Text = "ENTER HERE"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 16
Title.TextXAlignment = Enum.TextXAlignment.Left

-- USERS  DO NOT TOUCH THIS!
local titleGradient = Instance.new("UIGradient")
titleGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),
    ColorSequenceKeypoint.new(0.3, Color3.fromRGB(255, 150, 170)),
    ColorSequenceKeypoint.new(0.7, Color3.fromRGB(255, 100, 120)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 80, 100))
})
titleGradient.Parent = Title

-- USERS  DO NOT TOUCH THIS!
local titleGlow = Instance.new("ImageLabel")
titleGlow.Name = "TitleGlow"
titleGlow.Parent = Title
titleGlow.BackgroundTransparency = 1
titleGlow.Position = UDim2.new(0, -5, 0, -2)
titleGlow.Size = UDim2.new(1, 10, 1, 4)
titleGlow.Image = "rbxassetid://4996891970" -- Radial gradient
titleGlow.ImageColor3 = Color3.fromRGB(255, 80, 100)
titleGlow.ImageTransparency = 0.7
titleGlow.ZIndex = Title.ZIndex - 1

-- USERS  DO NOT TOUCH THIS!
local titleStroke = Instance.new("UIStroke")
titleStroke.Color = Color3.fromRGB(255, 100, 120)
titleStroke.Thickness = 1
titleStroke.Transparency = 0.7
titleStroke.Parent = Title

-- USERS  DO NOT TOUCH THIS!
spawn(function()
    local offset = 0
    while Title.Parent do
        offset = (offset + 0.001) % 1
        titleGradient.Offset = Vector2.new(offset, 0)
        
        -- Subtle pulse animation for the glow
        for i = 0, 10 do
            if not titleGlow.Parent then break end
            titleGlow.ImageTransparency = 0.7 + (math.sin(i/10 * math.pi) * 0.2)
            wait(0.1)
        end
    end
end)

-- USERS  DO NOT TOUCH THIS!
CloseButton = Instance.new("ImageButton")
CloseButton.Name = "CloseButton"
CloseButton.Parent = TopBar
CloseButton.BackgroundTransparency = 1
CloseButton.Position = UDim2.new(1, -30, 0.5, -10)
CloseButton.Size = UDim2.new(0, 20, 0, 20)
CloseButton.Image = "rbxassetid://6031094678" -- Close icon
CloseButton.ImageColor3 = Color3.fromRGB(255, 80, 100)

MinimizeButton = Instance.new("ImageButton")
MinimizeButton.Name = "MinimizeButton"
MinimizeButton.Parent = TopBar
MinimizeButton.BackgroundTransparency = 1
MinimizeButton.Position = UDim2.new(1, -60, 0.5, -10)
MinimizeButton.Size = UDim2.new(0, 20, 0, 20)
MinimizeButton.Image = "rbxassetid://6031090990" -- Minimize icon
MinimizeButton.ImageColor3 = Color3.fromRGB(200, 200, 200)

-- USERS  DO NOT TOUCH THIS!
TabContainer.Name = "TabContainer"
TabContainer.Parent = MainFrame
TabContainer.BackgroundColor3 = Color3.fromRGB(15, 15, 20) -- Match main frame color
TabContainer.BorderSizePixel = 0
TabContainer.Position = UDim2.new(0, 0, 0, 40)
TabContainer.Size = UDim2.new(0, 150, 1, -40)

-- USERS  DO NOT TOUCH THIS!
if TabContainer:FindFirstChild("UIGradient") then
    TabContainer:FindFirstChild("UIGradient"):Destroy()
end

local TabContainerCorner = Instance.new("UICorner")
TabContainerCorner.CornerRadius = UDim.new(0, 8)
TabContainerCorner.Parent = TabContainer

-- USERS  DO NOT TOUCH THIS!
local CornerFix = Instance.new("Frame")
CornerFix.Name = "CornerFix"
CornerFix.Parent = TabContainer
CornerFix.BackgroundColor3 = Color3.fromRGB(15, 15, 20) -- Match TabContainer color
CornerFix.BorderSizePixel = 0
CornerFix.Position = UDim2.new(1, -8, 0, 0)
CornerFix.Size = UDim2.new(0, 8, 0, 8)

-- USERS  DO NOT TOUCH THIS!
local tabHeader = Instance.new("Frame")
tabHeader.Name = "TabHeader"
tabHeader.Parent = TabContainer
tabHeader.BackgroundColor3 = Color3.fromRGB(15, 15, 20) -- Match TabContainer color
tabHeader.BorderSizePixel = 0
tabHeader.Position = UDim2.new(0, 0, 0, 0)
tabHeader.Size = UDim2.new(1, 0, 0, 30)

local headerText = Instance.new("TextLabel")
headerText.Name = "HeaderText"
headerText.Parent = tabHeader
headerText.BackgroundTransparency = 1
headerText.Position = UDim2.new(0, 15, 0, 0)
headerText.Size = UDim2.new(1, -15, 1, 0)
headerText.Font = Enum.Font.GothamBold
headerText.Text = "NAVIGATION"
headerText.TextColor3 = Color3.fromRGB(255, 80, 100)
headerText.TextSize = 11
headerText.TextXAlignment = Enum.TextXAlignment.Left

-- USERS  DO NOT TOUCH THIS!
local separator = Instance.new("Frame")
separator.Name = "Separator"
separator.Parent = TabContainer
separator.BackgroundColor3 = Color3.fromRGB(255, 80, 100) -- Cherry red color
separator.BorderSizePixel = 0
separator.Position = UDim2.new(0, 10, 0, 30)
separator.Size = UDim2.new(1, -20, 0, 1)
separator.Transparency = 0.2

-- USERS  DO NOT TOUCH THIS!
local separatorGradient = Instance.new("UIGradient")
separatorGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 80, 100)),
    ColorSequenceKeypoint.new(0.2, Color3.fromRGB(255, 100, 120)),
    ColorSequenceKeypoint.new(0.4, Color3.fromRGB(255, 80, 100)),
    ColorSequenceKeypoint.new(0.6, Color3.fromRGB(255, 100, 120)),
    ColorSequenceKeypoint.new(0.8, Color3.fromRGB(255, 80, 100)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 80, 100))
})
separatorGradient.Transparency = NumberSequence.new({
    NumberSequenceKeypoint.new(0, 0.8),
    NumberSequenceKeypoint.new(0.2, 0.2),
    NumberSequenceKeypoint.new(0.4, 0.8),
    NumberSequenceKeypoint.new(0.6, 0.2),
    NumberSequenceKeypoint.new(0.8, 0.8),
    NumberSequenceKeypoint.new(1, 0.8)
})
-- USERS  DO NOT TOUCH THIS!
separatorGradient.Offset = Vector2.new(-0.2, 0)
separatorGradient.Parent = separator

-- USERS  DO NOT TOUCH THIS!
local separatorGlow = Instance.new("ImageLabel")
separatorGlow.Name = "SeparatorGlow"
separatorGlow.Parent = separator
separatorGlow.BackgroundTransparency = 1
separatorGlow.Position = UDim2.new(0, -10, 0, -2)
separatorGlow.Size = UDim2.new(1, 20, 0, 5)
separatorGlow.Image = "rbxassetid://4996891970" -- Radial gradient
separatorGlow.ImageColor3 = Color3.fromRGB(255, 80, 100)
separatorGlow.ImageTransparency = 0.5
separatorGlow.ScaleType = Enum.ScaleType.Slice
separatorGlow.SliceCenter = Rect.new(10, 10, 10, 10)

-- USERS  DO NOT TOUCH THIS!
spawn(function()
   
    local offset = -0.2 
    local animationSpeed = 0.0008 
    
    while separator.Parent do

        offset = offset + animationSpeed
        
      
        if offset >= 0.8 then
            offset = -0.2 
        end
        
        separatorGradient.Offset = Vector2.new(offset, 0)
        game:GetService("RunService").Heartbeat:Wait()
    end
end)

-- Tab List with updated position
local TabList = Instance.new("ScrollingFrame")
TabList.Name = "TabList"
TabList.Parent = TabContainer
TabList.Active = true
TabList.BackgroundTransparency = 1
TabList.Position = UDim2.new(0, 0, 0, 40) 
TabList.Size = UDim2.new(1, 0, 1, -50) 
TabList.CanvasSize = UDim2.new(0, 0, 0, 0)
TabList.ScrollBarThickness = 2
TabList.ScrollBarImageColor3 = Color3.fromRGB(255, 80, 100)
TabList.ScrollBarImageTransparency = 0.8
TabList.AutomaticCanvasSize = Enum.AutomaticSize.Y

local TabListLayout = Instance.new("UIListLayout")
TabListLayout.Parent = TabList
TabListLayout.SortOrder = Enum.SortOrder.LayoutOrder
TabListLayout.Padding = UDim.new(0, 8) 

local TabListPadding = Instance.new("UIPadding")
TabListPadding.Parent = TabList
TabListPadding.PaddingLeft = UDim.new(0, 10)
TabListPadding.PaddingRight = UDim.new(0, 10)
TabListPadding.PaddingTop = UDim.new(0, 5)
TabListPadding.PaddingBottom = UDim.new(0, 5)

-- USERS  DO NOT TOUCH THIS!
ContentContainer.Name = "ContentContainer"
ContentContainer.Parent = MainFrame
ContentContainer.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
ContentContainer.BorderSizePixel = 0
ContentContainer.Position = UDim2.new(0, 150, 0, 40)
ContentContainer.Size = UDim2.new(1, -150, 1, -40)

-- USERS  DO NOT TOUCH THIS!
function CherryHub:CreateTab(name, icon)

    local tabContainer = Instance.new("Frame")
    tabContainer.Name = name.."Container"
    tabContainer.Parent = TabList
    tabContainer.BackgroundColor3 = Color3.fromRGB(25, 25, 30) 
    tabContainer.BorderSizePixel = 0
    tabContainer.Size = UDim2.new(1, 0, 0, 36)
    
-- USERS  DO NOT TOUCH THIS!
    local function createRipple(x, y)
        local ripple = Instance.new("Frame")
        ripple.Name = "Ripple"
        ripple.Parent = tabContainer
        ripple.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        ripple.BackgroundTransparency = 0.8
        ripple.BorderSizePixel = 0
        ripple.Position = UDim2.new(0, x - 5, 0, y - 5)
        ripple.Size = UDim2.new(0, 10, 0, 10)
        ripple.ZIndex = 10
        
        local rippleCorner = Instance.new("UICorner")
        rippleCorner.CornerRadius = UDim.new(1, 0)
        rippleCorner.Parent = ripple
        

        TweenService:Create(ripple, TweenInfo.new(0.5), {
            Size = UDim2.new(0, 150, 0, 150),
            Position = UDim2.new(0, x - 75, 0, y - 75),
            BackgroundTransparency = 1
        }):Play()
        
 
        game:GetService("Debris"):AddItem(ripple, 0.5)
    end
    
    local containerCorner = Instance.new("UICorner")
    containerCorner.CornerRadius = UDim.new(0, 6)
    containerCorner.Parent = tabContainer
    

    local gradient = Instance.new("UIGradient")
    gradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(32, 32, 37)),
        ColorSequenceKeypoint.new(1, Color3.fromRGB(28, 28, 33))
    })
    gradient.Rotation = 90
    gradient.Parent = tabContainer
    

    local stroke = Instance.new("UIStroke")
    stroke.Color = Color3.fromRGB(60, 60, 65)
    stroke.Thickness = 1
    stroke.Transparency = 0.7
    stroke.Parent = tabContainer
    
    local tabButton = Instance.new("TextButton")
    tabButton.Name = name.."Tab"
    tabButton.Parent = tabContainer
    tabButton.BackgroundTransparency = 1
    tabButton.Size = UDim2.new(1, 0, 1, 0)
    tabButton.Font = Enum.Font.GothamSemibold
    tabButton.Text = name
    tabButton.TextColor3 = Color3.fromRGB(200, 200, 200)
    tabButton.TextSize = 14
    tabButton.AutoButtonColor = false
    tabButton.TextXAlignment = Enum.TextXAlignment.Left
    

    local selectionIndicator = Instance.new("Frame")
    selectionIndicator.Name = "SelectionIndicator"
    selectionIndicator.Parent = tabContainer
    selectionIndicator.BackgroundColor3 = Color3.fromRGB(255, 80, 100)
    selectionIndicator.BorderSizePixel = 0
    selectionIndicator.Position = UDim2.new(0, 0, 0, 0)
    selectionIndicator.Size = UDim2.new(0, 3, 1, 0)
    selectionIndicator.Visible = false
    
    local indicatorCorner = Instance.new("UICorner")
    indicatorCorner.CornerRadius = UDim.new(0, 2)
    indicatorCorner.Parent = selectionIndicator
    
    local tabIcon
    if icon then
        tabIcon = Instance.new("ImageLabel")
        tabIcon.Name = "Icon"
        tabIcon.Parent = tabContainer
        tabIcon.BackgroundTransparency = 1
        tabIcon.Position = UDim2.new(0, 12, 0.5, -10)
        tabIcon.Size = UDim2.new(0, 20, 0, 20)
        tabIcon.Image = icon
        tabIcon.ImageColor3 = Color3.fromRGB(200, 200, 200)
        

        local iconGlow = Instance.new("ImageLabel")
        iconGlow.Name = "Glow"
        iconGlow.Parent = tabIcon
        iconGlow.BackgroundTransparency = 1
        iconGlow.Position = UDim2.new(0.5, -15, 0.5, -15)
        iconGlow.Size = UDim2.new(0, 30, 0, 30)
        iconGlow.Image = "rbxassetid://4996891970" -- Radial gradient
        iconGlow.ImageColor3 = Color3.fromRGB(255, 80, 100)
        iconGlow.ImageTransparency = 1 -- Start invisible
        iconGlow.ZIndex = tabIcon.ZIndex - 1
        

        tabButton.TextXAlignment = Enum.TextXAlignment.Left
        tabButton.Position = UDim2.new(0, 40, 0, 0)
        tabButton.Size = UDim2.new(1, -40, 1, 0)
    end
    

    local contentPage = Instance.new("ScrollingFrame")
    contentPage.Name = name.."Page"
    contentPage.Parent = ContentContainer
    contentPage.BackgroundTransparency = 1
    contentPage.BorderSizePixel = 0
    contentPage.Size = UDim2.new(1, 0, 1, 0)
    contentPage.CanvasSize = UDim2.new(0, 0, 0, 0)
    contentPage.ScrollBarThickness = 4
    contentPage.ScrollBarImageColor3 = Color3.fromRGB(255, 80, 100)
    contentPage.Visible = false
    contentPage.AutomaticCanvasSize = Enum.AutomaticSize.Y
    
    local contentPadding = Instance.new("UIPadding")
    contentPadding.Parent = contentPage
    contentPadding.PaddingLeft = UDim.new(0, 15)
    contentPadding.PaddingRight = UDim.new(0, 15)
    contentPadding.PaddingTop = UDim.new(0, 15)
    contentPadding.PaddingBottom = UDim.new(0, 15)
    
    local contentLayout = Instance.new("UIListLayout")
    contentLayout.Parent = contentPage
    contentLayout.SortOrder = Enum.SortOrder.LayoutOrder
    contentLayout.Padding = UDim.new(0, 10)
    

    local function selectTab()
   
        for _, child in pairs(ContentContainer:GetChildren()) do
            if child:IsA("ScrollingFrame") then
                child.Visible = false
            end
        end
        

        for _, child in pairs(TabList:GetChildren()) do
            if child:IsA("Frame") then
                -- Reset gradient
                if child:FindFirstChild("UIGradient") then
                    child.UIGradient.Color = ColorSequence.new({
                        ColorSequenceKeypoint.new(0, Color3.fromRGB(32, 32, 37)),
                        ColorSequenceKeypoint.new(1, Color3.fromRGB(28, 28, 33))
                    })
                end
                
              
                if child:FindFirstChild("UIStroke") then
                    child.UIStroke.Color = Color3.fromRGB(60, 60, 65)
                    child.UIStroke.Transparency = 0.7
                end
                
       
                if child:FindFirstChild("SelectionIndicator") then
                    child.SelectionIndicator.Visible = false
                end
                
              
                if child:FindFirstChild(child.Name:gsub("Container", "Tab")) then
                    child[child.Name:gsub("Container", "Tab")].TextColor3 = Color3.fromRGB(200, 200, 200)
                end
                
                
                if child:FindFirstChild("Icon") then
                    child.Icon.ImageColor3 = Color3.fromRGB(200, 200, 200)
                    if child.Icon:FindFirstChild("Glow") then
                        TweenService:Create(child.Icon.Glow, TweenInfo.new(0.3), {ImageTransparency = 1}):Play()
                    end
                end
            end
        end
        
       
        contentPage.Visible = true
        
       
        gradient.Color = ColorSequence.new({
            ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 100, 120)),
            ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 80, 100))
        })
        
   
        stroke.Color = Color3.fromRGB(255, 120, 140)
        stroke.Transparency = 0.5
        
    
        selectionIndicator.Visible = true
        selectionIndicator.Size = UDim2.new(0, 3, 0, 0)
        selectionIndicator.Position = UDim2.new(0, 0, 0.5, 0)
        TweenService:Create(selectionIndicator, TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {
            Size = UDim2.new(0, 3, 1, 0),
            Position = UDim2.new(0, 0, 0, 0)
        }):Play()
        
  
        tabButton.TextColor3 = Color3.fromRGB(255, 255, 255)
        
       
        if tabIcon then
            tabIcon.ImageColor3 = Color3.fromRGB(255, 255, 255)
            TweenService:Create(tabIcon, TweenInfo.new(0.3), {
                Position = UDim2.new(0, 14, 0.5, -10) -- Subtle movement
            }):Play()
            
            if tabIcon:FindFirstChild("Glow") then
                TweenService:Create(tabIcon.Glow, TweenInfo.new(0.5), {ImageTransparency = 0.7}):Play()
            end
        end
    end
    
    tabButton.MouseButton1Click:Connect(selectTab)
    
    
    tabContainer.MouseEnter:Connect(function()
        if not contentPage.Visible then
       
            TweenService:Create(gradient, TweenInfo.new(0.2), {
                Color = ColorSequence.new({
                    ColorSequenceKeypoint.new(0, Color3.fromRGB(55, 55, 60)),
                    ColorSequenceKeypoint.new(1, Color3.fromRGB(45, 45, 50))
                })
            }):Play()
            
          
            TweenService:Create(stroke, TweenInfo.new(0.2), {
                Transparency = 0.5
            }):Play()
            
         
            TweenService:Create(tabContainer, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 38)
            }):Play()
            
            if tabIcon then
              
                TweenService:Create(tabIcon, TweenInfo.new(0.2), {
                    Position = UDim2.new(0, 14, 0.5, -10)
                }):Play()
            end
        end
    end)
    
    tabContainer.MouseLeave:Connect(function()
        if not contentPage.Visible then
           
            TweenService:Create(gradient, TweenInfo.new(0.2), {
                Color = ColorSequence.new({
                    ColorSequenceKeypoint.new(0, Color3.fromRGB(45, 45, 50)),
                    ColorSequenceKeypoint.new(1, Color3.fromRGB(35, 35, 40))
                })
            }):Play()
            
          
            TweenService:Create(stroke, TweenInfo.new(0.2), {
                Transparency = 0.7
            }):Play()
            
         
            TweenService:Create(tabContainer, TweenInfo.new(0.2), {
                Size = UDim2.new(1, 0, 0, 36)
            }):Play()
            
            if tabIcon then
                
                TweenService:Create(tabIcon, TweenInfo.new(0.2), {
                    Position = UDim2.new(0, 12, 0.5, -10)
                }):Play()
            end
        end
    end)
    
    local tabFunctions = {}
    
    function tabFunctions:Select()
        selectTab()
    end
    
    return tabFunctions
end


local dragging
local dragInput
local dragStart
local startPos

local function updateDrag(input)
    local delta = input.Position - dragStart
    MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    Shadow.Position = MainFrame.Position
end

TopBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
        
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

TopBar.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
        dragInput = input
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if input == dragInput and dragging then
        updateDrag(input)
    end
end)


CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

MinimizeButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
    Shadow.Visible = MainFrame.Visible
end)

-- Dashboard/Home Tab
local homeTab = CherryHub:CreateTab("Home", "rbxassetid://6026568198")


local homePage = ContentContainer:FindFirstChild("HomePage")
if homePage then

    local welcomeFrame = Instance.new("Frame")
    welcomeFrame.Name = "WelcomeFrame"
    welcomeFrame.Parent = homePage
    welcomeFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
    welcomeFrame.BorderSizePixel = 0
    welcomeFrame.Size = UDim2.new(1, 0, 0, 100)
    welcomeFrame.LayoutOrder = 1
    
    local welcomeCorner = Instance.new("UICorner")
    welcomeCorner.CornerRadius = UDim.new(0, 8)
    welcomeCorner.Parent = welcomeFrame
    
    local welcomeGradient = Instance.new("UIGradient")
    welcomeGradient.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(40, 40, 45)),
        ColorSequenceKeypoint.new(1, Color3.fromRGB(30, 30, 35))
    })
    welcomeGradient.Rotation = 45
    welcomeGradient.Parent = welcomeFrame
    

    spawn(function()
        local rotation = 45
        while welcomeGradient.Parent do
            rotation = (rotation + 0.2) % 360
            welcomeGradient.Rotation = rotation
            wait(0.03)
        end
    end)
    
 -- ADD WELCOME TITLE HERE
    local welcomeTitle = Instance.new("TextLabel")
    welcomeTitle.Name = "WelcomeTitle"
    welcomeTitle.Parent = welcomeFrame
    welcomeTitle.BackgroundTransparency = 1
    welcomeTitle.Position = UDim2.new(0, 20, 0, 15)
    welcomeTitle.Size = UDim2.new(1, -40, 0, 30)
    welcomeTitle.Font = Enum.Font.SourceSansBold 
    welcomeTitle.Text = "ENTER HERE"
    welcomeTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
    welcomeTitle.TextSize = 20
    welcomeTitle.TextXAlignment = Enum.TextXAlignment.Left
    

    local titleStroke = Instance.new("UIStroke")
    titleStroke.Color = Color3.fromRGB(255, 100, 120)
    titleStroke.Thickness = 1
    titleStroke.Transparency = 0.7
    titleStroke.Parent = welcomeTitle
    

    local titleShadow = Instance.new("TextLabel")
    titleShadow.Name = "TitleShadow"
    titleShadow.Parent = welcomeTitle
    titleShadow.BackgroundTransparency = 1
    titleShadow.Position = UDim2.new(0, 1, 0, 1)
    titleShadow.Size = UDim2.new(1, 0, 1, 0)
    titleShadow.Font = Enum.Font.SourceSansBold
    titleShadow.Text = "ENTER HERE"
    titleShadow.TextColor3 = Color3.fromRGB(255, 80, 100)
    titleShadow.TextSize = 20
    titleShadow.TextTransparency = 0.8
    titleShadow.TextXAlignment = Enum.TextXAlignment.Left
    titleShadow.ZIndex = welcomeTitle.ZIndex - 1
    

    spawn(function()
        local originalText = welcomeTitle.Text
        welcomeTitle.Text = ""
        titleShadow.Text = ""
        
        for i = 1, #originalText do
            welcomeTitle.Text = string.sub(originalText, 1, i)
            titleShadow.Text = string.sub(originalText, 1, i)
            wait(0.03)
        end
        
   
        while welcomeTitle.Parent do
            for i = 0, 10 do
                titleStroke.Transparency = 0.7 + (math.sin(i/10 * math.pi) * 0.3)
                wait(0.1)
            end
        end
    end)
    
    local welcomeMessage = Instance.new("TextLabel")
    welcomeMessage.Name = "WelcomeMessage"
    welcomeMessage.Parent = welcomeFrame
    welcomeMessage.BackgroundTransparency = 1
    welcomeMessage.Position = UDim2.new(0, 20, 0, 50)
    welcomeMessage.Size = UDim2.new(1, -40, 0, 40)
    welcomeMessage.Font = Enum.Font.SourceSans 
    welcomeMessage.Text = "ENTER HERE"
    welcomeMessage.TextColor3 = Color3.fromRGB(200, 200, 200)
    welcomeMessage.TextSize = 14
    welcomeMessage.TextWrapped = true
    welcomeMessage.TextXAlignment = Enum.TextXAlignment.Left
    welcomeMessage.TextTransparency = 0.1 
    

    local titleGlow = Instance.new("ImageLabel")
    titleGlow.Name = "TitleGlow"
    titleGlow.Parent = welcomeTitle
    titleGlow.BackgroundTransparency = 1
    titleGlow.Position = UDim2.new(0, -10, 0, -5)
    titleGlow.Size = UDim2.new(1, 20, 1, 10)
    titleGlow.Image = "rbxassetid://4996891970" 
    titleGlow.ImageColor3 = Color3.fromRGB(255, 80, 100)
    titleGlow.ImageTransparency = 0.85
    titleGlow.ZIndex = welcomeTitle.ZIndex - 2
    
  
    spawn(function()
        while titleGlow.Parent do
            for i = 0, 20 do
                titleGlow.ImageTransparency = 0.85 + (math.sin(i/20 * math.pi) * 0.1)
                wait(0.1)
            end
        end
    end)
    

    local statsFrame = Instance.new("Frame")
    statsFrame.Name = "StatsFrame"
    statsFrame.Parent = homePage
    statsFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
    statsFrame.BorderSizePixel = 0
    statsFrame.Size = UDim2.new(1, 0, 0, 80)
    statsFrame.LayoutOrder = 2
    statsFrame.Position = UDim2.new(0, 0, 0, 110)
    
    local statsCorner = Instance.new("UICorner")
    statsCorner.CornerRadius = UDim.new(0, 8)
    statsCorner.Parent = statsFrame
    

    local statsLayout = Instance.new("UIListLayout")
    statsLayout.Parent = statsFrame
    statsLayout.FillDirection = Enum.FillDirection.Horizontal
    statsLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
    statsLayout.VerticalAlignment = Enum.VerticalAlignment.Center
    statsLayout.Padding = UDim.new(0, 15)
    
    -- EDIT STAT CARDS
    local function createStatCard(title, value, icon)
        local statCard = Instance.new("Frame")
        statCard.Name = title.."Card"
        statCard.Parent = statsFrame
        statCard.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
        statCard.BorderSizePixel = 0
        statCard.Size = UDim2.new(0, 120, 0, 60)
        
        local cardCorner = Instance.new("UICorner")
        cardCorner.CornerRadius = UDim.new(0, 6)
        cardCorner.Parent = statCard
        
        local cardStroke = Instance.new("UIStroke")
        cardStroke.Color = Color3.fromRGB(255, 80, 100)
        cardStroke.Thickness = 1
        cardStroke.Transparency = 0.8
        cardStroke.Parent = statCard
        
        local iconImage = Instance.new("ImageLabel")
        iconImage.Name = "Icon"
        iconImage.Parent = statCard
        iconImage.BackgroundTransparency = 1
        iconImage.Position = UDim2.new(0, 10, 0, 10)
        iconImage.Size = UDim2.new(0, 20, 0, 20)
        iconImage.Image = icon
        iconImage.ImageColor3 = Color3.fromRGB(255, 80, 100)
        
        local titleLabel = Instance.new("TextLabel")
        titleLabel.Name = "Title"
        titleLabel.Parent = statCard
        titleLabel.BackgroundTransparency = 1
        titleLabel.Position = UDim2.new(0, 40, 0, 10)
        titleLabel.Size = UDim2.new(1, -50, 0, 20)
        titleLabel.Font = Enum.Font.GothamSemibold
        titleLabel.Text = title
        titleLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
        titleLabel.TextSize = 12
        titleLabel.TextXAlignment = Enum.TextXAlignment.Left
        
        local valueLabel = Instance.new("TextLabel")
        valueLabel.Name = "Value"
        valueLabel.Parent = statCard
        valueLabel.BackgroundTransparency = 1
        valueLabel.Position = UDim2.new(0, 10, 0, 35)
        valueLabel.Size = UDim2.new(1, -20, 0, 20)
        valueLabel.Font = Enum.Font.GothamBold
        valueLabel.Text = "0"
        valueLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
        valueLabel.TextSize = 16
        valueLabel.TextXAlignment = Enum.TextXAlignment.Center
        
        
        spawn(function()
            local target = tonumber(value)
            local current = 0
            local increment = math.ceil(target / 50)
            
            while current < target do
                current = math.min(current + increment, target)
                valueLabel.Text = tostring(current)
                wait(0.02)
            end
        end)
        
        return statCard
    end
    
    -- EDIT/ADD stat cards (Beware of creating new statcards)
    createStatCard("DASHNAME1", "N/A", "rbxassetid://6026568198")
    createStatCard("DASHNAME2", "N/A", "rbxassetid://6031225819")
    createStatCard("DASHNAME3", "N/A", "rbxassetid://6031763426")
    
    -- Quick actions 
    local actionsFrame = Instance.new("Frame")
    actionsFrame.Name = "ActionsFrame"
    actionsFrame.Parent = homePage
    actionsFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
    actionsFrame.BorderSizePixel = 0
    actionsFrame.Size = UDim2.new(1, 0, 0, 150) -- Adjusted height
    actionsFrame.LayoutOrder = 3
    actionsFrame.Position = UDim2.new(0, 0, 0, 200)
    
    local actionsCorner = Instance.new("UICorner")
    actionsCorner.CornerRadius = UDim.new(0, 8)
    actionsCorner.Parent = actionsFrame
    
    local actionsTitle = Instance.new("TextLabel")
    actionsTitle.Name = "ActionsTitle"
    actionsTitle.Parent = actionsFrame
    actionsTitle.BackgroundTransparency = 1
    actionsTitle.Position = UDim2.new(0, 15, 0, 10)
    actionsTitle.Size = UDim2.new(1, -30, 0, 20)
    actionsTitle.Font = Enum.Font.GothamBold
    actionsTitle.Text = "Quick Actions"
    actionsTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
    actionsTitle.TextSize = 14
    actionsTitle.TextXAlignment = Enum.TextXAlignment.Left
    

    if actionsFrame:FindFirstChild("UIGridLayout") then
        actionsFrame:FindFirstChild("UIGridLayout"):Destroy()
    end
    
    if actionsFrame:FindFirstChild("UIPadding") then
        actionsFrame:FindFirstChild("UIPadding"):Destroy()
    end
    

    local function createActionButton(name, icon, posX, posY)
        local actionButton = Instance.new("TextButton")
        actionButton.Name = name.."Button"
        actionButton.Parent = actionsFrame
        actionButton.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
        actionButton.BorderSizePixel = 0
        actionButton.Text = ""
        actionButton.Position = UDim2.new(posX, 15, posY, 0)
        actionButton.Size = UDim2.new(0.5, -25, 0, 40)
        actionButton.AutoButtonColor = false
        actionButton.ClipsDescendants = true 
        
        local buttonCorner = Instance.new("UICorner")
        buttonCorner.CornerRadius = UDim.new(0, 6)
        buttonCorner.Parent = actionButton
        

        local innerGlow = Instance.new("UIStroke")
        innerGlow.Name = "InnerGlow"
        innerGlow.Color = Color3.fromRGB(255, 100, 120)
        innerGlow.Thickness = 1.5
        innerGlow.Transparency = 0.9
        innerGlow.Parent = actionButton
        
        local buttonIcon = Instance.new("ImageLabel")
        buttonIcon.Name = "Icon"
        buttonIcon.Parent = actionButton
        buttonIcon.BackgroundTransparency = 1
        buttonIcon.Position = UDim2.new(0, 15, 0.5, -10)
        buttonIcon.Size = UDim2.new(0, 20, 0, 20)
        buttonIcon.Image = icon
        buttonIcon.ImageColor3 = Color3.fromRGB(255, 80, 100)
        

        local iconGlow = Instance.new("ImageLabel")
        iconGlow.Name = "IconGlow"
        iconGlow.Parent = buttonIcon
        iconGlow.BackgroundTransparency = 1
        iconGlow.Position = UDim2.new(0.5, -15, 0.5, -15)
        iconGlow.Size = UDim2.new(0, 30, 0, 30)
        iconGlow.Image = "rbxassetid://4996891970" -- Radial gradient
        iconGlow.ImageColor3 = Color3.fromRGB(255, 80, 100)
        iconGlow.ImageTransparency = 0.85
        iconGlow.ZIndex = buttonIcon.ZIndex - 1
        
        local buttonText = Instance.new("TextLabel")
        buttonText.Name = "Text"
        buttonText.Parent = actionButton
        buttonText.BackgroundTransparency = 1
        buttonText.Position = UDim2.new(0, 45, 0, 0)
        buttonText.Size = UDim2.new(1, -55, 1, 0)
        buttonText.Font = Enum.Font.GothamSemibold
        buttonText.Text = name
        buttonText.TextColor3 = Color3.fromRGB(230, 230, 230)
        buttonText.TextSize = 14
        buttonText.TextXAlignment = Enum.TextXAlignment.Left
        

        local shine = Instance.new("Frame")
        shine.Name = "Shine"
        shine.Parent = actionButton
        shine.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        shine.BorderSizePixel = 0
        shine.Size = UDim2.new(0, 10, 1, 0)
        shine.Position = UDim2.new(-0.5, 0, 0, 0)
        shine.BackgroundTransparency = 0.9
        shine.ZIndex = actionButton.ZIndex + 1
        shine.Rotation = 20
        

        local function createRipple(x, y)
            local ripple = Instance.new("Frame")
            ripple.Name = "Ripple"
            ripple.Parent = actionButton
            ripple.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            ripple.BackgroundTransparency = 0.85
            ripple.BorderSizePixel = 0
            ripple.Position = UDim2.new(0, x - 5, 0, y - 5)
            ripple.Size = UDim2.new(0, 10, 0, 10)
            ripple.ZIndex = actionButton.ZIndex + 1
            
            local rippleCorner = Instance.new("UICorner")
            rippleCorner.CornerRadius = UDim.new(1, 0)
            rippleCorner.Parent = ripple
            

            TweenService:Create(ripple, TweenInfo.new(0.5), {
                Size = UDim2.new(0, 150, 0, 150),
                Position = UDim2.new(0, x - 75, 0, y - 75),
                BackgroundTransparency = 1
            }):Play()
            
 
            game:GetService("Debris"):AddItem(ripple, 0.5)
        end
        

        actionButton.MouseEnter:Connect(function()

            TweenService:Create(actionButton, TweenInfo.new(0.3), {
                BackgroundColor3 = Color3.fromRGB(50, 50, 55)
            }):Play()
            
    
            TweenService:Create(innerGlow, TweenInfo.new(0.3), {
                Transparency = 0.7
            }):Play()
            
          
            TweenService:Create(buttonIcon, TweenInfo.new(0.3), {
                Position = UDim2.new(0, 17, 0.5, -10), -- Subtle movement
                ImageColor3 = Color3.fromRGB(255, 100, 120) -- Brighter color
            }):Play()
            
            
            TweenService:Create(iconGlow, TweenInfo.new(0.3), {
                ImageTransparency = 0.7
            }):Play()
            
           
            TweenService:Create(shine, TweenInfo.new(0.5), {
                Position = UDim2.new(1.5, 0, 0, 0)
            }):Play()
        end)
        
        actionButton.MouseLeave:Connect(function()
            
            TweenService:Create(actionButton, TweenInfo.new(0.3), {
                BackgroundColor3 = Color3.fromRGB(40, 40, 45)
            }):Play()
            
            
            TweenService:Create(innerGlow, TweenInfo.new(0.3), {
                Transparency = 0.9
            }):Play()
            
           
            TweenService:Create(buttonIcon, TweenInfo.new(0.3), {
                Position = UDim2.new(0, 15, 0.5, -10), -- Reset position
                ImageColor3 = Color3.fromRGB(255, 80, 100) -- Reset color
            }):Play()
            
          
            TweenService:Create(iconGlow, TweenInfo.new(0.3), {
                ImageTransparency = 0.85
            }):Play()
            
        
            shine.Position = UDim2.new(-0.5, 0, 0, 0)
        end)
        
    
        actionButton.MouseButton1Down:Connect(function(x, y)
         
            local relativeX = x - actionButton.AbsolutePosition.X
            local relativeY = y - actionButton.AbsolutePosition.Y
            createRipple(relativeX, relativeY)
            
            
            TweenService:Create(actionButton, TweenInfo.new(0.1), {
                BackgroundColor3 = Color3.fromRGB(60, 60, 65),
                Size = UDim2.new(0.5, -25, 0, 38) -- Slightly smaller
            }):Play()
            
           
            TweenService:Create(buttonIcon, TweenInfo.new(0.1), {
                Size = UDim2.new(0, 18, 0, 18), -- Slightly smaller
                Position = UDim2.new(0, 16, 0.5, -9) -- Adjusted position
            }):Play()
        end)
        
        actionButton.MouseButton1Up:Connect(function()
           
            TweenService:Create(actionButton, TweenInfo.new(0.2), {
                BackgroundColor3 = Color3.fromRGB(50, 50, 55),
                Size = UDim2.new(0.5, -25, 0, 40) 
            }):Play()
            
            
            TweenService:Create(buttonIcon, TweenInfo.new(0.2), {
                Size = UDim2.new(0, 20, 0, 20), 
                Position = UDim2.new(0, 15, 0.5, -10) 
            }):Play()
        end)
        
        
        spawn(function()
            while actionButton.Parent do
                for i = 0, 10 do
                    if not iconGlow.Parent then break end
                    local transparency = iconGlow.ImageTransparency
                    local targetTransparency = transparency - 0.05 + (math.sin(i/10 * math.pi) * 0.05)
                    TweenService:Create(iconGlow, TweenInfo.new(0.5), {
                        ImageTransparency = targetTransparency
                    }):Play()
                    wait(0.5)
                end
            end
        end)
        
        return actionButton
    end
    
    -- EDIT QUICK ACTIONS HERE
    createActionButton("QACTION1", "rbxassetid://6031763426", 0, 0.25)
    createActionButton("QACTION2", "rbxassetid://6026568198", 0.5, 0.25)
    
    
    createActionButton("QACTION3", "rbxassetid://6034509993", 0, 0.55)
    createActionButton("QACTION4", "rbxassetid://6035047391", 0.5, 0.55)
end

-- Select Home tab by default
homeTab:Select()

return CherryHub

homeTab:Select()
