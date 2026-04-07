# 🚜 Realistic Engine Temperature (RET)
**Current Version:** 7.0.x  |  **Farming Simulator 25**

**Realistic Engine Temperature (RET)** is an advanced physics mod designed for Farming Simulator 25. It disables the native and utopian mechanical temperature of the base game, replacing it with a hyper-realistic thermodynamic model.

Whether you have an old diesel tractor, a vintage air-cooled harvester, or a top-of-the-line electric model, RET will simulate exactly how heat is generated, dissipated, and the potential breakdowns in the middle of the process!

---

## 🌟 Main Features

### 1. Active Thermodynamic System
Heat doesn't rise linearly. It is calculated every millisecond based on:
- **Engine Load:** Pulling a heavy plow uphill at 100% Load will generate extreme heat that pushes the mechanics to their limits.
- **RPMs / Idle:** Engines left idling generate only base heat. Revving them to the Redline in neutral generates friction and heat.
- **Weather and Wind:** Working on a cold rainy day decreases heat. Driving at 50 km/h generates natural wind cooling (Wind Cooling) that helps cool the engine regardless of the fan.

### 2. Three Distinct Engine Profiles (NEW in V7!)
Farming Simulator doesn't distinguish between engines, but RET does! The mod detects your tractor's consumption (Diesel, Methane, or Electric) and applies completely different physics:
*   🟢 **Water-Cooled (Standard):** The classic block with antifreeze and a thermostat. Keeps the engine between 80ºC and 90ºC. Uses a dynamic temperature valve.
*   💨 **Air-Cooled:** Ideal for classics (e.g., old Porsches). No thermal inertia! Cooling relies purely on the spinning of the engine-attached fan (RPMs). If you're doing very heavy PTO work with the tractor stationary, it will heat up dangerously fast!
*   ⚡ **Electric Vehicles (EV / Batteries):** Ignores 100ºC boiling limits. Operate within a tight thermal protection profile (20ºC - 65ºC). They don't generate heat when stationary, functioning purely based on the extreme effort of current discharge. They feature a BTMS with its own heating if in the cold and electrified ventilation.

### 3. Smart Valves and Thermostats
On a standard tractor (Water), the physics are controlled by a **Thermostat**. During the first minutes of the morning, it remains closed (0%) to retain heat in the cabin using a rich fuel injection (fast warmup). Upon reaching 85ºC, the valve dynamically opens in percentage to invoke the Central Radiator fans and halt the rise!

### 4. Mechanical Damage and Stochastic Failures (Overheating Breakdowns)
Is your tractor already showing significant wear on the repair screen? Get ready for the mechanical lottery!
The **Thermostat Valve can break down while moving** in an aging tractor:
*   **Stuck Open:** The tractor cannot maintain temperature and chronically runs cold (damaging cylinders under load).
*   **Stuck Closed:** Flow to the radiator is cut off. The water boils, the cabin alarm sounds, and the engine will suffer immediate damage until you pull over!

*(The severity and valve closure fluctuate percentage-wise with each percentage of vehicle damage).*

### 5. Cold Engine Stress Damage
Don't just grab the tractor at 6 AM and start plowing straight away!
The mod severely punishes the mechanics of tractors (and the repair wallet) that are pushed to the limit of RPMs or high Load levels while the temperature gauge is still in the cold zone! Warm up your tractor first!

### 6. Dirt Penalty (Radiator Sludge)
Working in the mud all day coats the machinery's fins. As the Dirt meter increases in FS25, the maximum cooling power of your radiator plummets, making summer jobs impossible without stopping in the sun.

---

## 🖥️ The Interface (Dynamic HUD)
The Mod injects smooth and useful text into the corner of the screen for visual monitoring (only when the engine is running):
- **Safe Max RPM:** Shows if you can push the throttle. Turns Red if you're hurting it!
- **HP and Adjustments:** The native horsepower recognized to generate heat (with active readings if you do Chiptuning at the Workshop!).
- **Load / Average Load:** The constant balance of your effort (current % and the Average of the last minute of work).
- **Valve:** Observe the exact percentage at which water transitions to the cooling panels.

Additionally, RET hijacks the Native Warnings system (Farming Simulator's flashing screen banner) alerting you when forcing work on a cold engine or at the limit of Overheating.

---

## 🛠️ Console Commands (For Advanced Users)
The system has memory per Tractor and synchronizes everything server-side for Multiplayer! You can open the game console with the `~` / `'` key and use the shortcuts below by typing `ret <command>`:

| Command | Action |
| :--- | :--- |
| `ret help` | Shows the help panel and all shortcuts. |
| `ret on` / `ret off` | Fully enables or disables the mod in the current save game. |
| `ret water` | Forces the tractor you are currently sitting in to use a Water-Cooled engine (Standard). |
| `ret air` | Forces the current tractor to ignore thermostats and be Air-Cooled. |
| `ret electric` | Forces the current tractor to use a tight Lithium thermal curve (EV Batteries). |
| `ret debug true` | Activates developer mode, spitting out the raw math of visual heat loss and absorption equations (+ and -) under the menu. |
| `ret load` / `ret save` | Instantly reads or forces saving of data to the XML file. |

---

## ⚙️ Uncompromised Customization
Are you a Hard-Roleplay server creator or a Physics Master? The Mod will create the physical `modSettings/RealisticEngineTemp/` folder in your game documents as soon as you enter the first save.
Inside the **`Config.xml`** file, you literally own the Laws of Physics. You can:
- Change passive heating rates in Degrees per Millisecond.
- Change at what Degree the valve enters alert mode and opens (e.g., from 85ºC to 95ºC).
- Change the heating Quotient of all electric batteries on the map!
*(Whenever the mod version is updated, the system retains your XML numbers and cleanly introduces only the keys from new versions - You will never lose your calibration again).*

## 🤝 Full Integration
Fully compatible not only with native Farming Simulator 25 but also tested for organic interconnection with other Famous Modding Mods, like the **Adjustable Engine Power** module. Where 10% to 20% increases from Chip Tuning will permanently multiply the unleashed heat inside the engine block, requiring larger fans!

Crafted with the most demanding farming Roleplayers in mind. Enjoy!
