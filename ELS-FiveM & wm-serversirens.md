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


# 🚨 Adding Custom Sirens in ELS-FiveM  

## 🎛️ Requirements  
To add or modify custom sirens, you’ll need **OpenIV** or another **AWC editing tool**.

---

## 📂 Step 1: Locate the Siren Files  
Navigate to the following directory in your **wm-serversirens folder**:  

```
dlc_wmsirens
```

---

## 📁 Step 2: Open the “oac” Folder  
Inside **`dlc_wmsirens`**, locate and open the **`oac`** folder.  

---

## 🎵 Step 3: Replace the `.wav` Files  
- Replace the existing `.wav` files with your **custom siren audio files**.  
- **⚠️ Important:** **Do NOT rename the files**—this is crucial for **WMServerSirens** to function properly.  

---

## 🔄 Step 4: Compile the `.AWC` File  
- After modifying the siren pack, locate the **`.oac`** file in the same folder.  
- Drag and drop it into **OpenIV** to compile your siren sounds into an `.AWC` file.  

---

## 🚀 Step 5: Replace the Default Siren Pack  
- Take the newly compiled `.AWC` file and move it into:  

```
dlc_wmserversirens
```

- Overwrite the existing siren pack **without changing the file name**.  

---

## 🏁 Step 6: Start Your Server & Enjoy!  
Restart your FiveM server and **test your new custom sirens**! Maybe even **celebrate with some fireworks**! 🎆🚓  

---

# 🔧 Configuring Sirens with ELS  
By default, custom sirens won’t work with every **ELS script**—a few tweaks are required.  

### 📥 Step 1: Request the Audio File  
At the top of your ELS script, request the **audio bank** to ensure the sirens load for all players:  

```lua
RequestScriptAudioBank("DLC_WMSIRENS\\SIRENPACK_ONE", false)
```

- If you only modified **Siren Pack One**, you only need to include this one.  
- If you modified multiple packs, add them as needed.  

---

### 🎶 Step 2: Playing the Custom Siren  
To play a **custom siren sound from a vehicle**, use this FiveM native function:  

```lua
PlaySoundFromEntity(-1, "SIREN_ALPHA", veh, "DLC_WMSIRENS_SOUNDSET", 0, 0)
```

Where:  
- **`veh`** = The vehicle the player is in (**Use:** `GetVehiclePedIsUsing(PlayerPedId())`).  

**Example:**  
In your **ELS script**, replace:  

```lua
VEHICLES_HORNS_SIREN_1
```

With:  

```lua
"SIREN_ALPHA"
```

**⚠️ Important:** You also need to update the script to use:  

```lua
"DLC_WMSERVERSIRENS_SOUNDSET"
```

as the custom DLC soundset when playing sounds from the entity.  

---

### 🛠️ Optional: Play Different Sirens for Different Vehicles  
To play the **correct siren** based on the vehicle, use an **if-statement** in your code to check the player's current vehicle and apply the correct sound.  

---

## 🔤 Siren Naming Convention  
All sirens in **WMServerSirens** follow the **phonetic alphabet** (e.g., **SIREN_ALPHA, SIREN_BRAVO, SIREN_CHARLIE**).  

This helps with **organization and future development**. A quick **Google search** will show the full phonetic alphabet if needed.  

---

## ✅ Conclusion  
You’re all set! 🎉 Your custom sirens are now in place, and your FiveM vehicles are sounding better than ever. Enjoy the ride! 🚔💨  
```
