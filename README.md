# SUPER SIMPLE 3D printer Time-lapse Automation

This project will allow you to take a picture at the end of every layer of your 3D print,
which will allow you to later on put them together in a scene using Adobe Premiere Pro.
This method will seemlessly show the extruder hovering above your print while it is being 
created. 

### Hardware and Software necessary

- One of the following 3D printers: Ender 3, Ender 3 Pro, Ender 3 V2  
     > https://www.amazon.com/s?k=ender+3&ref=nb_sb_noss_1
- Sony remore shutter  
     > https://www.amazon.com/gp/product/B00MULZSNQ/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1   
- Ultimaker Cura 4.0 and above  
     > https://ultimaker.com/software/ultimaker-cura  
- Sony camera (I use my Sony A7ii)  
- Micro SD card  
- 22g of filament 

### Steps

1. download the following file and print it with supports (touching the build plate).  
      > https://raw.githubusercontent.com/miniquinox/Time-lapse_Automation/main/Shutter%20Structure.gcode
2. Save the GCODE in your MicroSD card.
3. Insert the MicroSD card and click on "Print from SD card". Select "Structure.gcode".  
      > **Make sure to have at least 23 grams of PLA loaded on your printer**  
4. After it is done printing, wait for the bed to cool down and remove the print and its supports carefully.  
      > **Do the following steps regardless even if you have a printer added already**  
5. Open Ultimaker Cura and click on Settings > Printer > Add printer
6. Click on "Add a non-networked printer"
7. Go down to "Creality3D" and select your printer
8. On the right menu, change Printer name to "Time-lapse"  
9. Delete the content in the "Start-Gcode" cell and replace it with the following:
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
  
10. Delete the content in the "End-Gcode" cell and replace it with the following:
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

11. You have now added your printer with timelapse settings!  
12. Go ahead and open the following link:  
      > https://raw.githubusercontent.com/miniquinox/Time-lapse_Automation/main/CustomTimelapse.py
13. Right click on the code and select "Save As". Save it as "CustomTimelapse" and file type "Python". Put this file in your desktop.
14. On Cura, click on Help > Show configuration folder
15. Open the scripts folder and move here your CustomTimelapse.py file that you saved in your desktop.
16. Restart Cura (Close and open)
17. Click on Extensions > Post Processing > Modify gcode
18. Click on Add Script and select "Quino's timelapse". Once it's added, hit close and load your 3D model
##### DONE!

## STEPS FROM NOW ON
- Simply put the shutter in its structure in the following way:  
  <img src="https://raw.githubusercontent.com/miniquinox/Projects/master/20210225_153939.jpg" width="400" height="300">
- Connect it to your camera and you're ready to shoot amazing timelapses!!
- The process looks like this:  
  <img src="https://github.com/miniquinox/Projects/blob/master/20210225_162330_1.gif" height="400">
- Here is how your timelapses will look like:  
  <img src="https://github.com/miniquinox/Projects/blob/master/Final%20Video%203%201080p_2.gif" width="400" height="225">

