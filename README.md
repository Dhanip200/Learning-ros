# Learning-ros
I am learning ros and gazebo so this is a public liberary documenting my journy
I Set-up a WSL in my windows laptop
Then installed ros2-jazzy , jazzy was not being supported by normal windows(it might get updated in the future).So i am running it on the  VcXsrv server 
Step 1 go to offecial website of VcXser server install it extrect it and u should be good to go.
Go to Xlaunc in your laptop (it is automatically installed) select 1 large window, go select start no client and the check all the boxes and in additional information write -nowgl.
On CMD write wsl --shutdown to turn it off just in case.
Open ubuntu in your laptop(It is WSL) and write 
do this 
Action Plan: Final Comprehensive Troubleshooting for "Unable to Open Display"
Follow these steps exactly and in order. Do not skip any, even if you think you've done them already.

Part 1: Prepare Windows and VcXsrv (Crucial Steps)

Close ALL WSL Terminals: Ensure no WSL windows are open.

Fully Shut Down WSL: Open a Windows Command Prompt (search for cmd in Start Menu) and run:

DOS

wsl --shutdown
Wait for it to complete.

End ALL VcXsrv Processes:

Go to your Windows System Tray (bottom right, near the clock; click the ^ icon to show hidden icons).
Right-click on every single 'X' icon that belongs to VcXsrv (there might be more than one from previous attempts). Select "Exit" or "Quit".
Open Windows Task Manager (Ctrl+Shift+Esc). Go to the "Details" tab. Look for vcxsrv.exe. If you see any instances, select them and click "End task". Ensure no vcxsrv.exe processes are running.
Launch XLaunch (VcXsrv) with Precise Settings:

Find and launch XLaunch from your Windows Start Menu.
Screen 1: Display settings
Select: "Multiple windows".
Click "Next >".
Screen 2: Client startup
Select: "Start no client".
Click "Next >".
Screen 3: Extra settings (ABSOLUTELY CRITICAL)
CHECK the box next to "Native opengl".
CHECK the box next to "Disable access control". (This is the most common reason for your "unable to open display" error if VcXsrv is running).
In the "Additional parameters for VcXsrv" text box, type exactly: -nowgl. (Make sure there is a space before the hyphen).
Click "Next >".
Screen 4: Finish configuration
Click "Finish".
Verify VcXsrv is Running: Look for the 'X' icon in your Windows system tray. It must be there. Hover over it to confirm it says "XLaunch :0.0" or "Xming Server :0.0". If it's not there, VcXsrv did not start correctly, and you need to restart this step from "End ALL VcXsrv Processes".
Configure NVIDIA Control Panel for vcxsrv.exe:
Search for "Windows Defender Firewall with Advanced Security" in the Windows Start menu and open it.
Check "Inbound Rules":
Look for rules named something like "VcXsrv Inbound" and "WSL Inbound" (or whatever you named them).
Ensure they are "Enabled", "Action" is "Allow the connection", and "Profile" includes "Private" (and ideally "Public" and "Domain" for broader compatibility).
If you don't see them, create new ones: "New Rule..." -> "Program" -> Browse to C:\Program Files\VcXsrv\vcxsrv.exe (and repeat for C:\Windows\System32\wsl.exe).
Check "Outbound Rules": Do the same verification/creation process for outbound rules for vcxsrv.exe and wsl.exe.
REBOOT Your Entire Windows Machine: This is essential for all graphics and network changes to fully take effect.
(Make sure u have correct driver and u should be fine)
GO to bash and type  export DISPLAY=<your ip address>
check it using this commond  echo $DISPLAY
the print this glxinfo | grep "OpenGL version"
glxinfo | grep "OpenGL renderer"
output e.g.=OpenGL version string: 4.2 (Compatibility Profile) Mesa 24.2.8-1ubuntu1~24.04.1
OpenGL renderer string: D3D12 (AMD Radeon(TM) Graphics)


Now finally running the turtal bot on the jazzy
 by running this =source /opt/ros/jazzy/setup.bash
export TURTLEBOT3_MODEL=waffle
