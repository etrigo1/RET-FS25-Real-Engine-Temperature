[🇵🇹 Ler em Português](README.pt.md) | 🇺🇸 English

# 🚜 Realistic Engine Temperature (RET)

| | Version | Status |
|:---:|:---|:---:|
| 🟢 | **8.2.0** — Stable Release | [![Stable](https://img.shields.io/badge/Status-Stable-brightgreen)](https://github.com/etrigo1/RET-FS25-Real-Engine-Temperature/releases) |

**Farming Simulator 25**

**Realistic Engine Temperature (RET)** is an advanced physics mod designed for Farming Simulator 25. It disables the native and utopian mechanical temperature of the base game, replacing it with a hyper-realistic thermodynamic model.

Whether you have an old diesel tractor, a vintage air-cooled harvester, or a top-of-the-line electric model, RET will simulate exactly how heat is generated, dissipated, and the potential breakdowns in the middle of the process!

---

## 🌟 Main Features

### 1. Active Thermodynamic System
Heat doesn't rise linearly. It is calculated every millisecond based on:
- **Engine Load:** Pulling a heavy plow uphill at 100% Load will generate extreme heat that pushes the mechanics to their limits.
- **RPMs / Idle:** Engines left idling generate only base heat. Revving them to the Redline in neutral generates friction and heat.
- **Weather and Wind:** Working on a cold rainy day decreases heat. Driving at 50 km/h generates natural wind cooling (Wind Cooling) that helps cool the engine regardless of the fan.
- **DFCO (Deceleration Fuel Cut-Off):** When coasting downhill in gear without accelerating, the engine stops injecting fuel and generates no heat — just like a real engine.

### 2. Five Vehicle Profiles
Farming Simulator doesn't distinguish between engines, but RET does! The mod detects your vehicle's consumption (Diesel, Methane, or Electric) and applies completely different physics. You can also override the detected profile at any time with a console command:
*   🟢 **Water-Cooled (Standard):** The classic block with antifreeze and a thermostat. Keeps the engine between 80ºC and 90ºC. Uses a dynamic temperature valve.
*   💨 **Air-Cooled:** Ideal for classics (e.g., old Porsches). No thermal inertia! Cooling relies purely on the spinning of the engine-attached fan (RPMs). If you're doing very heavy PTO work with the tractor stationary, it will heat up dangerously fast!
*   ⚡ **Electric Vehicles (EV / Batteries):** Ignores 100ºC boiling limits. Operate within a tight thermal protection profile (20ºC - 65ºC). They don't generate heat when stationary, functioning purely based on the extreme effort of current discharge. They feature a BTMS with its own heating if in the cold and electrified ventilation.
*   🚗 **Car (Light Vehicle) *(NEW in v8.1!)***:  Modern passenger cars warm up much faster (~2 min to 80ºC). The thermostat valve opens between 80ºC and 87ºC. Cooling is purely wind-driven while moving (no fan), and an **independent electric fan** activates only when temperature reaches 95ºC. All cold and overheating damage rules apply equally.
*   🚫 **No-RET *(NEW in v8.1!)***:  Completely removes a specific vehicle from RET's simulation. The game's native temperature takes over. Only the RET title bar is shown in grey when debug mode is active.

### 3. Smart Valves and Thermostats
On a standard tractor (Water), the physics are controlled by a **Thermostat**. During the first minutes of the morning, it remains closed (0%) to retain heat using a rich fuel injection (fast warmup). Upon reaching 85ºC, the valve dynamically opens in percentage to invoke the Central Radiator fans and halt the rise!

### 4. Advanced Damage System & Real Breakdowns *(NEW in v8!)*
RET introduces three separate layers of mechanical consequence:

**Layer 1 — Thermostat Valve Failure (Stochastic):**
When your tractor accumulates enough wear (configurable, default 70%), a dice roll determines if the **thermostat valve physically breaks**:
*   **Stuck Open:** The tractor cannot retain heat and chronically runs cold, damaging cylinders under load.
*   **Stuck Closed:** Flow to the radiator is completely blocked. The water boils fast, the cabin alarm sounds, and the engine suffers immediate damage until you stop!

Repairing the tractor at the workshop resets the failure state and gives the valve another chance.

**Layer 2 — Overheating Stall:**
If the engine temperature climbs **5ºC above the damage threshold** (default: above 115ºC), there is a growing random chance the engine will **stall itself** to prevent catastrophic failure. The hotter it gets, the higher the chance per second.

**Layer 3 — Damage-Driven Stall & Start Lock *(NEW in v8!)***:
The overall tractor condition now directly affects the engine's ability to run:
*   **Between 80% and 95% damage:** The engine has a growing random chance of **stalling mid-work**. The closer to 95%, the higher the probability per second.
*   **Above 95% damage:** The engine **cannot be started at all**. Take the tractor to the workshop before it's too late!

*(All thresholds and probabilities are fully configurable in Config.xml).*

### 5. Cold Engine Stress Damage
Don't just grab the tractor at 6 AM and start plowing straight away!
The mod severely punishes tractors pushed to the RPM limit or high Load levels while the temperature gauge is still cold. Warm up your tractor first!

### 6. Dirt Penalty (Radiator Sludge)
Working in the mud all day coats the machinery's fins. As the Dirt meter increases in FS25, the maximum cooling power of your radiator plummets, making summer jobs impossible without stopping in the sun.

---

## 🖥️ The Interface (Adaptive HUD)
The Mod injects smooth and useful text into the corner of the screen for visual monitoring (only when the engine is running). The HUD adapts automatically to the vehicle profile:
- **Safe Max RPM:** Shows if you can push the throttle. Turns Red if you're hurting it!
- **HP and Adjustments:** The native horsepower recognized to generate heat (with active readings if you do Chiptuning at the Workshop!).
- **Load / Average Load:** The constant balance of your effort (current % and the Average of the last minute of work).
- **Valve:** Observe the exact percentage at which water transitions to the cooling panels.
- **Fan *(Car only)*:** Shows the electric fan status — `Fan: OFF` (blue) when temperature is below 95ºC, `Fan: ON (70%)` (green) when the fan is actively cooling.
- **Dirt %:** Total radiator dirt level and the active cooling penalty it is applying.
- **No-RET vehicles:** Only the title bar is shown in grey, indicating the vehicle is excluded from simulation.

Additionally, RET hijacks the Native Warnings system (Farming Simulator's flashing screen banner) alerting you when forcing work on a cold engine or at the limit of Overheating. Battery overheat warnings are also fully localized in your game language.

---

## 🛠️ Console Commands (For Advanced Users)
The system has memory per Tractor and synchronizes everything server-side for Multiplayer! You can open the game console with the `~` / `'` key and use the shortcuts below by typing `ret <command>`:

| Command | Action |
| :--- | :--- |
| `ret help` | Shows the help panel and all shortcuts. |
| `ret on` / `ret off` | Fully enables or disables the mod in the current save game. |
| `ret water` | Forces the vehicle you are sitting in to use a Water-Cooled engine (Standard). |
| `ret air` | Forces the current vehicle to ignore thermostats and be Air-Cooled. |
| `ret electric` | Forces the current vehicle to use a tight Lithium thermal curve (EV Batteries). |
| `ret car` | Forces the current vehicle to use the **Car profile** (thermostat + electric fan). *(New in v8.1)* |
| `ret noret` | **Excludes** the current vehicle from RET entirely. Native temperature takes over. *(New in v8.1)* |
| `ret debug true` | Activates developer mode, spitting out the raw math of visual heat loss and absorption equations (+ and -) under the menu. |
| `ret load` / `ret save` | Instantly reads or forces saving of data to the XML file. |

---

## ⚙️ Uncompromised Customization & Config.xml Guide

Are you a Hard-Roleplay server creator or a Physics Master? The Mod will create the physical `modSettings/RealisticEngineTemp/Config.xml` file in your game documents as soon as you enter the first save. Inside this file, you literally own the Laws of Physics.

> **Smart Upgrade System:** Whenever the mod version is updated, the system retains your XML numbers and cleanly introduces only the keys from new versions. You will never lose your calibration again.

### 📚 Config.xml Variable Reference

---

#### 🌐 General & Multiplayer

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `enableMultiplayerSync` | bool | `true` | Syncs engine temperatures between all players on the server. |
| `enableDataLogging` | bool | `false` | Exports real-time engine telemetry to a local `.csv` file (for analysis in Excel). |
| `logIntervalMs` | number | `1000` | How often (in ms) a telemetry line is saved to the CSV. |

---

#### 🖥️ HUD & Debug

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `debugMode` | bool | `false` | Enables the on-screen debug HUD with all live physics values. |
| `hud_ShowTitle` | bool | `true` | Shows the RET title bar and multiplayer mode on screen. |
| `hud_ShowTempRPM` | bool | `true` | Shows the current temperature and RPM. |
| `hud_ShowValve` | bool | `true` | Shows the thermostat valve opening percentage. |
| `hud_ShowFlow` | bool | `true` | Shows heat generation and dissipation rates (Gen/Pas/Rad). |
| `hud_ShowEff` | bool | `true` | Shows engine load and dirt penalty. |
| `hud_ShowLimits` | bool | `true` | Shows safe max RPM and HP (with chiptuning if active). |
| `hud_ShowFan` | bool | `true` | Shows the electric fan status line (Car profile only). |
| `uiRefreshRateBaseMs` | number | `500` | Master HUD refresh interval in milliseconds. |

---

#### 🔥 General Physics

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `globalSpeed` | number | `1.0` | Global multiplier for all physics speed (1.0 = real-time). |
| `refAmbientTemp` | number | `20.0` | Reference ambient temperature (ºC) used in all calculations. |
| `minRpmForHeat` | number | `250` | Minimum RPM for the engine to be considered "running" and generating heat. |
| `warmupFastMultiplier` | number | `2.0` | Cold-start heat multiplier below 60ºC (simulates rich fuel injection). |
| `autoCompensateWarmup` | bool | `true` | Automatically adjusts base heat so total warmup time is respected even with cold multiplier active. |

---

#### 🌡️ Thermostat (Water-Cooled Engine)

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `thermoStart` | number | `85.0` | Temperature (ºC) at which the thermostat valve starts opening. |
| `thermoFull` | number | `90.0` | Temperature (ºC) at which the thermostat valve is fully open. |
| `timeToWarmupIdle` | number | `8.0` | Minutes to warm up from ambient (20ºC) to `thermoStart` at idle. |
| `timeToOverheatLoad` | number | `12.0` | Minutes to go from `thermoFull` to `damageStart` at 100% load. |
| `timeToCoolDown` | number | `120.0` | Minutes for the engine to cool from `thermoStart` to ambient. |
| `damageStart` | number | `110.0` | Temperature (ºC) at which the engine starts taking damage. |
| `ambientHeatingModifier` | number | `0.0` | Extra heat influence per ºC of real weather above reference (0.0 = off). |
| `ambientCoolingModifier` | number | `0.05` | Cooling slowdown per ºC of weather above reference (0.05 = 5% per degree). |
| `windCoolingMultiplier` | number | `0.02` | Extra radiator efficiency per km/h of driving speed (2% per km/h). |

---

#### ⚡ Electric Vehicles (EV/Battery)

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `ev_thermoStart` | number | `25.0` | Temperature (ºC) at which the BTMS starts cooling the battery pack. |
| `ev_thermoFull` | number | `35.0` | Temperature (ºC) at which the BTMS cooling is at maximum. |
| `ev_optimalTemp` | number | `20.0` | Ideal battery temperature. The BTMS heats up to this when cold. |
| `ev_damageStart` | number | `65.0` | Temperature (ºC) at which the batteries start taking damage. |

---

#### 💨 Air-Cooled Engine

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `air_fanCoolingMultiplier` | number | `1.0` | Multiplier for fan-driven cooling power (scales with RPM + wind). |

---

#### 🚗 Car Profile *(New in v8.1)*

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `car_thermoStart` | number | `80.0` | Temperature (ºC) at which the car thermostat starts opening. |
| `car_thermoFull` | number | `87.0` | Temperature (ºC) at which the car thermostat is fully open. |
| `car_warmupTime` | number | `2.0` | Minutes to warm up from ambient temperature to `car_thermoStart`. |
| `car_windCoolingMultiplier` | number | `0.05` | Cooling gain per km/h while driving (radiator wind effect). |
| `car_fanOnTemp` | number | `95.0` | Temperature (ºC) at which the electric fan activates (independent of the valve). |
| `car_fanPower` | number | `0.70` | Electric fan cooling power as a fraction of `cooling_power_max` (70%). |

---

#### 🔧 Cold Engine Damage

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `enableColdRpmDamage` | bool | `true` | Engine takes damage if RPMs exceed the safe limit while cold. |
| `enableColdLoadDamage` | bool | `true` | Engine takes damage if load exceeds the safe limit while cold. |
| `coldDamageTempThreshold` | number | `60.0` | Temperature (ºC) below which cold damage rules apply. |
| `maxColdDamagePerSec` | number | `0.01` | Max damage applied per second while running cold at limit. |
| `limitRpmAtRef` | number | `0.60` | Max safe RPM as a fraction of max RPM when at ambient temp (60%). |
| `limitLoadAtRef` | number | `0.50` | Max safe load fraction when engine is cold (50%). |

---

#### 💥 Thermostat Failure & Overheating Stall

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `enableDamageEffects` | bool | `true` | Enables the thermostat valve failure system. |
| `damageStartThreshold` | number | `0.70` | Tractor damage level (0–1) that triggers the thermostat failure roll. |
| `thermostatFailChance` | number | `0.50` | Probability (0–1) that the thermostat physically fails when damage crosses the threshold. |
| `damageFullFailure` | number | `0.90` | Damage level at which thermostat failure severity reaches 100%. |
| `enableOverheatStall` | bool | `true` | Engine can stall if temperature exceeds `damageStart` + delta. |
| `overheatStallStartDelta` | number | `5.0` | Degrees above `damageStart` before stall risk begins (default: 115ºC). |
| `overheatStallChancePerSec` | number | `0.015` | Base chance per second of stalling when critically overheated (1.5%/s). |

---

#### 🚨 Damage-Driven Stall & Start Lock *(New in v8)*

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `enableDamageStall` | bool | `true` | Engine can stall or refuse to start based on tractor wear level. |
| `damageStallThreshold` | number | `0.80` | Damage level (0–1) at which random mid-work stalling begins (80%). |
| `damageStallChancePerSec` | number | `0.010` | Base stall chance per second between 80% and 95% damage (1%/s). |
| `damageNoStartThreshold` | number | `0.95` | Damage level at which the engine **cannot be started at all** (95%). |

---

#### 🔗 Mod Integrations

| Variable | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `integ_AEP_Enabled` | bool | `true` | Enables integration with the *Adjustable Engine Power* (AEP) mod. |
| `integ_AEP_heatStage1` | number | `1.10` | Heat multiplier for AEP Stage 1 chiptuning (+10%). |
| `integ_AEP_heatStage2` | number | `1.15` | Heat multiplier for AEP Stage 2 chiptuning (+15%). |
| `integ_AEP_heatStage3` | number | `1.20` | Heat multiplier for AEP Stage 3 chiptuning (+20%). |

---

## 🌍 Language Support
RET is fully localized in the following languages:
🇬🇧 English | 🇵🇹 Portuguese | 🇩🇪 German | 🇫🇷 French | 🇪🇸 Spanish | 🇺🇦 Ukrainian

---

## 🤝 Full Integration
Fully compatible not only with native Farming Simulator 25 but also tested for organic interconnection with other Famous Modding Mods, like the **Adjustable Engine Power** module. Where 10% to 20% increases from Chip Tuning will permanently multiply the unleashed heat inside the engine block, requiring larger fans!

Crafted with the most demanding farming Roleplayers in mind. Enjoy!

