choco feature enable -n allowGlobalConfirmation

choco install notepadplusplus
choco install opera
cinst git

# IIS
cinst -s WindowsFeatures IIS-WebServerRole
cinst -s WindowsFeatures IIS-WebServer
cinst -s WindowsFeatures IIS-WebServerManagementTools
cinst -s WindowsFeatures IIS-ApplicationDevelopment
cinst -s WindowsFeatures IIS-Performance
cinst -s WindowsFeatures IIS-HealthAndDiagnostics
cinst -s WindowsFeatures IIS-CommonHttpFeatures
cinst -s WindowsFeatures IIS-NetFxExtensibility45
cinst -s WindowsFeatures IIS-ASPNET45
choco install urlrewrite

# Install SQL Server Express edition with SQL authentication turned on and the password for the SA user being the computer name
choco install sql-server-express -ia -o "/SECURITYMODE=SQL /SAPWD=$Env:Computername"

# MSBuild.exe
choco install visualstudio2019buildtools --package-parameters "--includeRecommended --add Microsoft.VisualStudio.Workload.WebBuildTools"
choco install netfx-4.6.1-devpack
# add MSBuild to PATH
$oldpath = [Environment]::GetEnvironmentVariable("PATH", "Machine")
$newpath = "$oldpath;C:\Program Files (x86)\Microsoft Visual Studio\2019\BuildTools\MSBuild\Current\Bin\amd64\"
[Environment]::SetEnvironmentVariable("PATH", $newpath, "Machine")

# 7-zip needed for superize
choco install 7zip

# BoxStarter extensions
#Install-WindowsUpdate -getUpdatesFromMS -acceptEula -SuppressReboots
#Set-WindowsExplorerOptions -EnableShowHiddenFilesFoldersDrives  -EnableShowFileExtensions -EnableShowFullPathInTitleBar
