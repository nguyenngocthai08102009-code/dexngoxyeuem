-- =================================================================
-- SCRIPT: spdex-codetestv1
-- STYLE: Redz-like UI (Trọng lực Hub Starter)
-- =================================================================

-- Hủy UI cũ nếu chạy lại script để không bị trùng màn hình
if game:GetService("CoreGui"):FindFirstChild("spdex_codetestv1") then
    game:GetService("CoreGui")["spdex_codetestv1"]:Destroy()
end

-- TẠO SCREEN GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "spdex_codetestv1"
ScreenGui.Parent = game:GetService("CoreGui")
ScreenGui.ResetOnSpawn = false

-- KHUNG CHÍNH (MAIN FRAME)
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 320, 0, 180)
MainFrame.Position = UDim2.new(0.5, -160, 0.4, -90)
MainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 25) -- Màu tối chuẩn Redz
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true -- Cho phép kéo thả UI trên màn hình
MainFrame.Parent = ScreenGui

-- Bo góc cho Khung chính
local MainCorner = Instance.new("UICorner")
MainCorner.CornerRadius = UDim.new(0, 10)
MainCorner.Parent = MainFrame

-- Viền nét cho Khung chính (Stroke)
local MainStroke = Instance.new("UIStroke")
MainStroke.Thickness = 1.5
MainStroke.Color = Color3.fromRGB(255, 0, 100) -- Viền hồng/đỏ neon nổi bật
MainStroke.Parent = MainFrame

-- THANH TIÊU ĐỀ (HEADER)
local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Size = UDim2.new(1, 0, 0, 35)
Title.BackgroundTransparency = 1
Title.Text = "  spdex-codetestv1"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 16
Title.Font = Enum.Font.SourceSansBold
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = MainFrame

-- NÚT ĐÓNG NHANH (CLOSE BUTTON)
local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 30, 0, 30)
CloseButton.Position = UDim2.new(1, -35, 0, 3)
CloseButton.BackgroundTransparency = 1
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(255, 80, 80)
CloseButton.TextSize = 18
CloseButton.Font = Enum.Font.SourceSansBold
CloseButton.Parent = MainFrame

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- KHU VỰC CHỨA CÁC NÚT (CONTAINER)
local Container = Instance.new("Frame")
Container.Name = "Container"
Container.Size = UDim2.new(1, -20, 1, -55)
Container.Position = UDim2.new(0, 10, 0, 45)
Container.BackgroundTransparency = 1
Container.Parent = MainFrame

-- Layout tự động sắp xếp các nút
local UIListLayout = Instance.new("UIListLayout")
UIListLayout.Parent = Container
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0, 10)

-- =================================================================
-- NÚT 1: TRỌNG LỰC HUB (Chức năng chính của em đây)
-- =================================================================
local GravityBtn = Instance.new("TextButton")
GravityBtn.Name = "GravityBtn"
GravityBtn.Size = UDim2.new(1, 0, 0, 45)
GravityBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
GravityBtn.BorderSizePixel = 0
GravityBtn.Text = "⚡ Trọng lực Hub"
GravityBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
GravityBtn.TextSize = 15
GravityBtn.Font = Enum.Font.SourceSansSemibold
GravityBtn.Parent = Container

-- Bo góc nút
local BtnCorner = Instance.new("UICorner")
BtnCorner.CornerRadius = UDim.new(0, 8)
BtnCorner.Parent = GravityBtn

-- Hiệu ứng rê chuột vào nút (Hover)
GravityBtn.MouseEnter:Connect(function()
    GravityBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 100) -- Đổi sang màu hồng neon khi rê chuột
end)

GravityBtn.MouseLeave:Connect(function()
    GravityBtn.BackgroundColor3 = Color3.fromRGB(30, 30, 40) -- Về lại màu cũ
end)

-- SỰ KIỆN CLICK: Xóa UI hiện tại và kích hoạt Gravity Hub
GravityBtn.MouseButton1Click:Connect(function()
    -- Thông báo nhỏ trước khi chuyển giao diện
    GravityBtn.Text = "Đang tải Gravity Hub..."
    task.wait(0.5)
    
    -- 1. Xóa sạch UI spdex-codetestv1 cũ đi cho đỡ vướng
    ScreenGui:Destroy()
    
    -- 2. Thực thi loadstring của Gravity Hub
    pcall(function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Dev-GravityHub/BloxFruit/refs/heads/main/Main.lua"))()
    end)
end)

-- Gửi thông báo đã bật script thành công
game:GetService("StarterGui"):SetCore("SendNotification", {
    Title = "spdex-codetestv1",
    Text = "Đã tải giao diện test thành công! Nhấn Trọng lực Hub để quẩy.",
    Duration = 4
})
