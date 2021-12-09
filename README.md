
# Cài đặt và sử dụng Powershell + Oh my Posh + Windows Terminal để làm việc với môi trường windows trên windows 10/ 11.
Thật ra bài viết này mình lấy cảm hứng từ video của [@Takuya](https://github.com/craftzdog), chủ kênh youtube [devaslife](https://www.youtube.com/channel/UC7yZ6keOGsvERMp2HaEbbXQ)
Video của anh này là toàn bộ quá trình cài đặt và setting của anh ấy, tuy nhiên anh ấy làm video dạng ASMR nên gõ tay hết tất cả config :)) quá mất thời gian vì vậy mình viết lại bài này ngắn gọn để các bạn có thể cài đặt và setting trong vài phút mà vẫn có 1 pwsh đủ dùng. Bản thân mình chủ yếu sử dụng zsh trên Ubuntu 20.04 WSL2, powershell chủ yếu để khi cần thì nhìn nó đẹp hơn, và có thể sắp tới phải động vào dotnet thì mới dùng tới. Chúc các bạn có 1 pwsh như ý muốn.

## Chúng ta muốn gì?
Về cơ bản, chúng ta chỉ muốn làm cho cái terminal powershell đẹp hơn mà thôi.
  - Một terminal có thể cài đặt và custom như các terminal xịn xò trên Linux hay MacOS
  - Command line installer [scoop](https://scoop.sh)
  - Prompt theme engine with [oh-my-posh](https://ohmyposh.dev/)
  - Terminal Icons - Folder and file icons
  - z: zumping tool
  
## Bắt đầu thôi

## Bước 1:
  - Chúng ta cần cài đặt Windows Terminal và PowerShell từ Microsoft Store
  - Đơn giản chỉ cần mở app Store lên tìm kiếm và ấn Get.

## Bước 2: Setting Powershell
  - Setting 1 chút trong Windows Terminal để powershell trông OKe hơn
    - Ở cửa sổ Windows Terminal, ấn `Ctr + ,` để mở Settings
    - Chọn PowerShell ở navbar bên trái sau đó chọn Appearance, chọn Font (hãy chọn 1 Nerd Font bất kì) và Color Scheme mà bạn thích
    - Kéo xuống dưới và enable Acrylic lên, chỉnh mức opacity mong muốn để có cửa sổ Terminal trong suốt.
    - Save changes và restart lại Windows Terminal
  - Cài đặt [scoop](https://scoop.sh): 1 command-line installer trên powershell.
  - Cài đặt neovim: `scoop install neovim gcc`
  - Cài đặt curl, sudo và jq: `scoop install curl sudo jq`

## Bước 3: Cài đặt các Module trên Powershell để làm đẹp và mạnh hơn chính nó
Ở bước này, chúng ta sẽ cài đặt 1 vài module, các bạn chỉ cần copy và paste vào powershell những lệnh sau:
```
Install-Module posh-git -Scope CurrentUser -Force
Install-Module oh-my-posh -Scope CurrentUser -Force
Install-Module -Name Terminal-Icons -Scope CurrentUser -Force
Install-Module -Name z -Scope CurrentUser -Force
Install-Module PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```
Sau đó chạy 2 lệnh sau để setup cho PSReadLine gợi ý  theo history
```
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView
```
Cài đặt fzf và PSfzf
```
scoop install fzf
Install-Module -Name PSfzf -Scope CurrentUser -Force
```

## Bước 4: Tạo file config cho powershell và chọn theme
- Mở folder home của bạn (C:\\Users\<username>)
- Tạo folder **.config**
- Tạo folder *powershell* trong **.config**
- tạo file **user_profile.ps1** và paste content từ file [này](.config/powershell/user_profile.ps1)
- import file user profile của bạn vào trong powershell user_profile:
  - Thủ công: Mở Folder **Documnents\PowerShell** và mở file Microsoft.PowerShell_profile.ps1 lên và thêm dòng sau: `. $env:USERPROFILE\.config\powershell\user_profile.ps1`
  - hoặc dùng vim: 
    - gõ `nvim $PROFILE.CurrentUserCurrentHost`
    - thêm dòng `. $env:USERPROFILE\.config\powershell\user_profile.ps1` vào và save file lại (Gõ *i* để insert, paste sau đó ESC :wq ENTER)
  - Awesome, thử khởi động lại terminal của bạn và mở powershell xem sao!
  - Để chọn theme cho powershell, vào [đây](https://ohmyposh.dev/docs/themes)
  - Thích theme nào thì gõ `Set-PoshPrompt <theme_name>`, thử **rainbow** xem nhé =))))

## Thanks for reading!
Nếu các bạn muốn tìm hiểu rõ hơn là nó hoạt động thế nào thì hãy xem video của a Takuya và đọc thêm về Powershell, scoop cũng như ohmyposh nhé! Mình chỉ muốn làm 1 hướng dẫn ngắn gọn để setup nhanh thôi.