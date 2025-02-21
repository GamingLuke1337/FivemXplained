# Handling.meta

## Where does the Handlings Folder come from?

It originally came from [Myleycyrusvirus](https://github.com/Myleycyrusvirus) [mcv-vehiclemetas](https://github.com/Myleycyrusvirus/mcv-vehiclemetas). I plan on adding missing vehicles from the latest Updates

## Where does the Tutorial come from?

This tutorial was taken from the deleted GTA5mods forum thread (https://forums.gta5-mods.com/topic/3842/tutorial-handling-meta/). I reuploaded it and made improvements from my own experience. If anyone wants the original forum thread: https://forums.gta5-mods.com/topic/3842/tutorial-handling-meta.

Special thanks to V4D3R for writing the original guide in the first place.


## What is the Handling.meta?

**Handling.meta** is a file in GTA V that, like in previous GTA games, controls the handling and physics of vehicles.

Located in:
```
xxxx\common\data
```

Examples:
```
Grand Theft Auto V\mods\update\update.rpf\common\data
Grand Theft Auto V\mods\update\x64\dlcpacks\mpbiker\dlc.rpf\common\data
```

This can be useful for new modders who have trouble understanding the parameters.

---

## 1. Parameters

### 1.1. Physical Attributes

These represent a vehicle's physical proportions in the game.

#### handlingName
- Used by the vehicles.meta, to identify the handling line of the particular vehicle.
- Any text no more than 14 characters can be used. Vanilla vehicles use uppercase letters by default.
- **Example:** `ADDER`, `DINGHY`

#### fMass
- The weight of the vehicle. Values should be given in **kilograms**.
- Used when the vehicle collides with another vehicle or a non-static object.

#### fInitialDragCoeff
- Sets the drag coefficient of the vehicle. Increase to simulate aerodynamic drag.
- **Value:** 10-120

#### fPercentSubmerged
- The percentage of the vehicle's "floating height" after it falls into the water, before sinking.
- **Default:** 85% for vanilla land vehicles.
- **Example:** `0.70` (70%)

#### vecCentreOfMassOffset
- Shifts the center of gravity in meters from side to side.
- **Values:**
  - X: -10.0 to 10.0. Positive values move the center of gravity right.
  - Y: -10.0 to 10.0. Positive values move the center of gravity forwards.
  - Z: -10.0 to 10.0. Positive values move the center of gravity upwards.

#### vecInertiaMultiplier
- I have no idea what this means. If someone knows, please let me know.
- **Values:**
  - X: -10.0 to 10.0.
  - Y: -10.0 to 10.0.
  - Z: -10.0 to 10.0.

---

### 1.2. Transmission

These values represent the vehicle's straight-line performance.

#### fDriveBiasFront
```xml
fDriveBiasFront value=“0.000000” = RWD

fDriveBiasFront value=“0.350000” = AWD 30/70 split

fDriveBiasFront value=“0.500000” = AWD 50/50 split

fDriveBiasFront value=“0.750000” = AWD 70/30 split

fDriveBiasFront value=“1.000000” = FWD
```

#### nInitialDriveGears
- Determines how many forward speeds/gears a vehicle's transmission contains.
- **Values:** 1 or more.

#### fInitialDriveForce
- Modifies the game's calculation of drive force (from the output of the transmission).
- **Values:** 0.01 - 2.0 and above.

---

### 1.3. Wheel Traction

These attributes describe how the vehicle behaves when cornering, accelerating, and decelerating.

#### fTractionCurveMax
- Cornering grip of the vehicle as a multiplier of the tire surface friction.

#### fTractionCurveMin
- Accelerating/braking grip of the vehicle as a multiplier of the tire surface friction.

#### fLowSpeedTractionLossMult
- How much traction is reduced at low speed.
- **Values:**
  - 0.0 = Normal traction.
  - Lower values = Less burnout, less sliding.
  - Higher values = More burnout.

---

### 1.4. Suspension

These attributes determine a vehicle's system of springs and shock absorbers.

#### fSuspensionForce
- Affects how strong suspension is.

#### fSuspensionCompDamp
- Damping during strut compression.
- **Bigger values = stiffer suspension.**

#### fSuspensionReboundDamp
- Damping during strut rebound.
- **Bigger values = stiffer suspension.**

#### fAntiRollBarForce
- Larger numbers = less body roll.

---

### 1.5. Damage

#### fCollisionDamageMult
- Multiplies the game's calculation of damage to the vehicle by collision.

#### fWeaponDamageMult
- Multiplies the game's calculation of damage to the vehicle by weapons.

#### fDeformationDamageMult
- Multiplies the game's calculation of deformation damage.

#### fEngineDamageMult
- Multiplies the game's calculation of damage to the engine, causing explosion or engine failure.
- **Values:** 0.0 - 10.0

---

### 1.6. Misc

#### fSeatOffsetDistX, Y, Z
- Controls seat offsets relative to vehicle body.

#### strModelFlags
- Written in HEX. Each digit represents a vehicle characteristic.

#### AIHandling
- Determines AI driving behavior.
- **Options:**
  - AVERAGE
  - CRAP
  - TRUCK
  - SPORTS_CAR

---

## 2. SubHandlingData

SubHandlingData contains handling profiles for specific vehicle types.

#### Example of a vehicle with no SubHandlingData:
```xml
<SubHandlingData>
    <Item type="NULL" />
    <Item type="NULL" />
    <Item type="NULL" />
</SubHandlingData>
```

---

### 2.1. CBoatHandlingData

Attributes for boats.

#### fRudderOffsetSubmerge
- Vertical offset of the propeller from the bone when determining if submerged or not.

#### fRudderOffsetForce
- Vertical offset of the propeller from the bone when force applied.

---

### 2.2. CBikeHandlingData

Attributes for bikes.

#### fLeanFwdCOMMult, fLeanBakCOMMult
- Modifies how much the rider leans forward/backward.

#### fWheelieBalancePoint, fStoppieBalancePoint
- Determines balance points for wheelies and stoppies.

---

### 2.3. CFlyingHandlingData

Attributes for aircraft.

#### fThrust
- The power of the engines.
- **Higher values = Faster aircraft.**

#### fFormLiftMult
- Base lift factor that’s independent of the wing’s attack angle.

---

### 2.4. CVehicleWeaponHandlingData

Attributes for vehicle-mounted weapons.

#### Example:
```xml
<WeaponSeats>0</WeaponSeats>
```

- Seat number that controls the weapon.
  - 0 = Driver’s seat.
  - Values: 0 - 8.

---

### 2.5. CSubmarineHandlingData

Attributes for submarines.

#### fPitchMult, fYawMult, fRollMult
- Controls submarine movement dynamics.

---

### 2.6. CTrailerHandlingData

Attributes for trailers.

#### fPosConstraintMassRatio
- Makes the trailer appear either heavier or lighter than the towing vehicle without changing the real mass.

---

## Final Notes

This guide is a work in progress. If you have any insights or additional information about handling.meta, please contribute! 🚀

**Happy modding!**
