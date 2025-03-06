# 🔧 How to Customize Your Horn in ELS-FiveM  

Here’s how you can customize your horn in ELS-FiveM! 🚗📢  

## 📂 1. Open the `client/util.lua` file  
Locate the file in your ELS-FiveM directory and open it with a text editor.  

## ✏️ 2. Edit the Code  
Go to **line 297** and replace the existing line with the following code:  

```lua
PlaySoundFromEntity(h_soundID_veh[veh], getVehicleVCFInfo(veh).sounds.mainHorn.audioString, veh, "DLC_WMSIRENS_SOUNDSET", 0, 0)
```

## 📁 3. Modify the `car_name.xml` File  
- Open the **VCF directory** and find the corresponding `car_name.xml` file.  
- Locate the **`SOUNDS` tag** and set the **`AudioString`** of **`MainHorn`** to the name of the sound source you configured in **WM-ServerSirens**.  

## ✅ 4. Save & Enjoy!  
Save all changes and restart your game – your new horn is now active! 🎉🚘  
