<#############################################################
CREATED BY: mike hartman
CONTACT: michael.hartman0@gmail.com
CONTACT: https://thepc.co
CONTACT: https://github.com/Cosmo121
LATEST VERSION: https://github.com/Cosmo121/Active-Directory
#############################################################>

# Import the Active Directory module
Import-Module ActiveDirectory

# Function for File Explorer prompt
Function Get-ServerFile ($defaultDirectory)
{
    [system.reflection.assembly]::LoadWithPartialName("System.windows.forms") | Out-Null

    $OpenFileDialog = New-Object System.Windows.Forms.OpenFileDialog
    $OpenFileDialog.InitialDirectory = $defaultDirectory
    $openFileDialog.Filter = "TXT (*.txt) | *.txt"
    $openFileDialog.ShowDialog() | Out-Null
    $openFileDialog.FileName
}

# Get the txt file for the user's to be added
$usersFile = Get-ServerFile "C:\"

# Open the text file and read the list of users
$users = Get-Content $usersFile

# Get the name of the Active Directory group to add the users to
$groupName = "Test-Group_One"

# Loop through the list of users and add them to the group
foreach ($user in $users) {
  Add-ADGroupMember -Identity $groupName -Members $user
}
