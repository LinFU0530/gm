# 偵測的軟體名稱
$processName = "wmplayer"
# ps檔位置
$scriptToRun = "C:\monitor_mp3.ps1"
# message
$message = "GM!!!!!!!!!!!!!!"

while ($true) {
    if (Get-Process -Name $processName -ErrorAction SilentlyContinue) {
        Write-Output "$processName is running. Executing $scriptToRun..."
        powershell -File "C:\notify.ps1" -token $token -message $message
    } else {
        Write-Output "$processName is not running. Waiting for it to start..."
    }
     Start-Sleep -Seconds 1 # 自行設定時間1為1秒偵測一次
}
