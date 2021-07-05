# destreamer_build
將 github.com/snobu/destreamer 專案編譯後的存檔

# 下載「未開放下載的 Microsoft Stream 影片」的方法
> 大多數公司上傳至 Microsoft Stream 的影片會因隱私權政策緣故，除了管理員外禁止下載以防止外流。若僅個人使用或純粹備存用途，可參考下述流程以進行影片備份。

1. 先使用「管理者權限」開啟 PowerShell，安裝 Chocolatey 後，再透過 Chocolatey 快速安裝必要相依套件。
> Chocolatey 官網：https://community.chocolatey.org/

  - 安裝 Chocolatey

```powershell
> Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

  - 透過 Chocolatey 安裝可編譯 github.com/snobu/destreamer 的相依套件

```powershell
> choco install -y ffmpeg nodejs.install git.install
```

  - 非必要但可順便安裝的影片下載套件

```powershell
> choco install -y youtube-dl
```

2. 開始編譯 github.com/snobu/destreamer 社群套件，同樣使用 PowerShell 進行。

```powershell
> cd $env:USERPROFILE\Documents\
> git clone https://github.com/snobu/destreamer
> cd destreamer
> npm install
> npm run build
```

3. 編譯完成 destreamer 後，即可使用 Powershell 下載 Microsoft Stream 影片（過程中會使用 Chromium 瀏覽器輸入密碼），下方以下載「中華電信總公司 Outlook 移轉緣由影片」為例。
> 更多 destreamer 指令參數可參考官網：https://github.com/snobu/destreamer

```powershell
> cd $env:USERPROFILE\Documents\destreamer\
> .\destreamer.ps1  -u 您中華電信的帳號@cht.com.tw -i "https://web.microsoftstream.com/video/53afbf3b-ca26-4a1e-861f-4f26a39012ae"
```

4. 下載好的影片預設會出現在資料夾 `$env:USERPROFILE\Documents\destreamer\videos`、`%USERPROFILE%\Documents\destreamer\videos` 裡。
