# DJIMavic3Mapping
A tool to convert QGroundControl generated .kml files into DJI Fly ready .kmz files.

# How to Use:
### I've made a video tutorial that you can watch [here](https://www.youtube.com).
## Steps:
* Download and install [Python](https://www.python.org/) or a [Python Interpreter](https://play.google.com/store/apps/details?id=org.qpython.qpy3&hl=en_US) (if on mobile devices)
* Download and install [QGroundControl](http://qgroundcontrol.com/)
1. Create a dummy DJI Fly Waypoint Mission
2. Create a mission using QGroundControl:
   1. To get an accurate Ground Resolution (pixel/centimeter) ratio and Photo Interval reading, use these settings:
   2. In the **Mission Start** tab, under **Vehicle Info**, set the desired **Hover Speed** (it has to match your **Waypoint Mission Speed** that has to be set in the DJI Fly App)
   3. In the **Survey** tab and in the **Camera** tab, use these settings for the Main Camera (Hasselblad):
      1. **Sensor**: 17.3 * 13 mm
      2. **Image**: 5290 * 3956 px
      3. **Focal Length**: 12.3 mm
   4. These for the Zoom Camera:
      1. **Sensor**: 6.4 * 4.8 mm
      2. **Image**: 4000 * 3000 px
      3. **Focal Length**: 29.85 mm
   5. Delete the **Takeoff** tab
   6. Select the **Overlap Percentage** or **Ground Resolution**
   7. **IF** you want the drone to stop and hover when taking every picture, click on **Options** and check **Hover and Capture Image**
   8. Change every other setting to fit your needs
   9. Click on **File** and select **Save Mission Waypoints As KML…**, choose the directory and save
      * **IF** you are using an Android device **AND** the Android conversion script, by default you should save the KML file in **"/storage/emulated/0/Downloads/"**
3. Run the Python script and follow its instructions:
   10. Drag & Drop the KML file (if you’re not using the Android script, in that case the script will automatically use the latest .kml file in the Downloads directory)
   11. Choose if the drone has to hover for each waypoint (You can always change this behavior later in the DJI Fly App)
   12. Copy the generated KMZ file to the last created folder in **“/storage/emulated/0/Android/data/dji.go.v5/files/waypoint/”** on Android or **“FILES/DJI File/wayline_mission/”** on IOS (I tried automating the Android script to copy and rename the file, but since Android 10, apps can’t access the Android/data folder anymore)
   13. Delete the previous KMZ file in the folder
   14. Copy the folder name
   15. Rename the new KMZ file to the folder name (maintain the “.kmz” file extension)
4. Restart **DJI Fly**
5. Select the last mission (the dummy mission) (The thumbnail is not updated yet)
6. Set the correct **Speed** (the same as **Hover Speed** in QGroundControl)
7. Set the correct **Altitude** if it's not the one you chose
8. **FLY**

## Known Issues
* IF YOU EDIT THE MISSION IN ANY WAY, EVEN IF YOU DON’T SAVE THOSE CHANGES, ONCE YOU OPEN THE DJI FLY APP AGAIN YOU’LL PROBABLY SEE A GRAPHICS ISSUE. DO NOT WORRY, IT’S JUST A GRAPHICS BUG, THE MISSION WILL WORK AS INTENDED
* Sometimes Waypoints may appear to be facing the wrong direction. I'm pretty sure it's another graphics issue, but I can't confirm
* The converted file generated with the "Hover and Take Picture" option with the Python script doesn't work properly yet, I believe it's fixable but I haven't figured out a solution yet
* Height issue, probably related to relative/absolute height mismatch
