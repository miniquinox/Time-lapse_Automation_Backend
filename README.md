# SUPER SIMPLE Time-lapse Automation

This project will allow you to take a picture at the end of every layer of your 3D print,
which will allow you to later on put them together in a scene using Adobe Premiere Pro.
This method will seemlessly show the extruder hovering above your print while it is being 
created. 

### Hardware and Software necessary

- One of the following 3D printers: Ender 2, Ender 3 Pro, Ender 3 V2
- 22g of filament
- Ultimaker Cura 4.0 and above
- Micro SD card

### Files to download

- 3D model
- Script

### Steps

1. Open the following link and copy all of its content (CTRL+A to select all, then CTRL+C to copy).  
      > https://raw.githubusercontent.com/miniquinox/Time-lapse_Automation/main/Shutter%20Structure.gcode
3. Open Notepad and paste with CTRL+V. Then save the file as "Structure.gcode".
4. Put this file in your MicroSD card.
5. Insert the MicroSD card and click on "Print from SD card". Select "Structure.gcode".  
      > **Make sure to have at least 23 grams of PLA loaded on your printer**  
5. After it is done printing, wait for the bed to cool down and remove the print and its supports carefully.  
      > **Do the following steps regardless even if you have a printer added already**  
6. Open Ultimaker Cura and click on Settings > Printer > Add printer
7. Click on "Add a non-networked printer"
8. Go down to "Creality3D" and select your printer
9. On the right menu, change Printer name to "Time-lapse"  
**10. Delete the content in the "Start-Gcode" cell and replace it with the following:**
  > ; Custom Start G-code for Time-lapse  
G92 E0 ; Reset Extruder  
G28 ; Home all axes  
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed  
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position  
G1 X0.1 Y185.0 Z0.3 F1500.0 E15 ; Draw the first line  
G1 X0.4 Y185.0 Z0.3 F5000.0 ; Move to side a little  
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line  
G92 E0 ; Reset Extruder  
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed  
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish  
  
**11. Delete the content in the "End-Gcode" cell and replace it with the following:**
> G91 ;Relative positioning\n  
G1 E-2 F2700 ;Retract a bit\n  
G1 E-2 Z0.2 F2400 ;Retract and raise Z\n  
G1 X5 Y5 F3000 ;Wipe out  
G1 Z10 ;Raise Z more  
G90 ;Absolute positionning  
G1 X120 Y185 ;Present print  
M106 S0 ;Turn-off fan  
M104 S0 ;Turn-off hotend  
M140 S0 ;Turn-off bed  
M84 X Y E ;Disable all steppers but Z  

12. You have now added your printer with timelapse settings!  
13. Go ahead and open the following link:  
      > https://raw.githubusercontent.com/miniquinox/Time-lapse_Automation/main/CustomTimelapse.py
14. Right click on the code and select "Save As". Save it as "CustomTimelapse" and file type "Python". Put this file in your desktop.
15. On Cura, click on Help > Show configuration folder
16. Open the scripts folder and move here your CustomTimelapse.py file that you saved in your desktop.
17. Restart Cura (Close and open)
18. Click on Extensions > Post Processing > Modify gcode
19. Click on Add Script and select "Quino's timelapse". Once it's added, hit close and load your 3D model
##### DONE!
21. 
