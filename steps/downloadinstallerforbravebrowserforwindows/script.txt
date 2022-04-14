# Script Variables
$downloadLink = "https://brave-browser-downloads.s3.brave.com/latest/brave_installer-x64.exe"
$fileLocation = "c:\software\"
$installer = "brave_installer-x64.exe"
$software = "Brave"
$installedApplication = "c:\Program Files\BraveSoftware\Brave-Browser\Application\brave.exe"

# Check if the software is already installed.
$installed = (Test-Path $installedApplication)

if($installed) 
{
	Write-Host "'$software' is already installed."
} 
else 
{
# Download the installer
    Write-Host "Downloading the '$software' installer..."
    if (-not (Test-Path $fileLocation)) 
    {
        New-Item -ItemType "directory" -Path "$fileLocation"
    }
    Invoke-WebRequest $downloadLink -OutFile $fileLocation$installer
    Get-Item $fileLocation$installer
}
