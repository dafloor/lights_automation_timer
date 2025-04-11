# Bewegingslicht met Timer (Geavanceerd) / Motion-Activated Lighting with Timer (Advanced)

Deze Home Assistant blueprint creëert een geavanceerde automatisering voor bewegingsgestuurde verlichting met een timer. Het biedt optionele dag- en nachtmodi met verschillende scènes, ondersteuning voor meerdere bewegingssensoren, extra configureerbare condities en de mogelijkheid om te kiezen wat er gebeurt wanneer de timer afloopt (uitschakelen, dimmen of een scène activeren).

This Home Assistant blueprint creates an advanced automation for motion-activated lighting with a timer. It offers optional day and night modes with different scenes, support for multiple motion sensors, extra configurable conditions, and the ability to choose what happens when the timer expires (turn off, dim, or activate a scene).

## Functies / Features

* **Meerdere Bewegingssensoren / Multiple Motion Sensors:** Trigger de automatisering met beweging van één of meerdere sensoren. / Trigger the automation with motion from one or more sensors.
* **Licht(en) of Scène(s) / Light(s) or Scene(s):** Bedien individuele lampen of activeer complete scènes. / Control individual lights or activate entire scenes.
* **Configureerbare Timer / Configurable Timer:** Stel eenvoudig de duur in (in minuten) dat het licht na de laatste beweging aan moet blijven. / Easily set the duration (in minutes) the light should stay on after the last motion.
* **Optionele Dag- en Nachtmodi / Optional Day and Night Modes:** Definieer specifieke starttijden en scènes voor de dag- en nachtperiode. / Define specific start times and scenes for the day and night periods.
* **Extra Condities / Extra Conditions:** Voeg optionele condities toe (zoals lichtniveau, status van andere apparaten, etc.) waaraan voldaan moet worden voordat de automatisering wordt uitgevoerd. / Add optional conditions (like light level, status of other devices, etc.) that must be met before the automation runs.
* **Actie bij Timer Afloop / Action on Timer Expiry:** Kies wat er gebeurt wanneer de timer afloopt: de lichten uitschakelen, dimmen naar een bepaald percentage, of een specifieke scène activeren. / Choose what happens when the timer expires: turn off the lights, dim them to a specific percentage, or activate a specific scene.

## Vereisten / Requirements

* Een werkende Home Assistant installatie. / A working Home Assistant installation.
* Geconfigureerde bewegingssensoren (`binary_sensor` met `device_class: motion`). / Configured motion sensors (`binary_sensor` with `device_class: motion`).
* Geconfigureerde lichten (`light` domain) en/of scènes (`scene` domain). / Configured lights (`light` domain) and/or scenes (`scene` domain).
* Een geconfigureerde `timer` entiteit die de brandtijd zal beheren. / A configured `timer` entity that will manage the light-on duration.

## Hoe deze Blueprint te gebruiken / How to Use This Blueprint

1.  **Importeer de Blueprint / Import the Blueprint:**
    * In Home Assistant ga naar `Instellingen` -> `Automatiseringen & Scènes` -> `Blueprints`. / In Home Assistant navigate to `Settings` -> `Automations & Scenes` -> `Blueprints`.
    * Klik op de knop `+ Blueprint importeren` (rechtsonder). / Click the `+ Import Blueprint` button (bottom right).
    * Plak de URL van dit `bewegingslicht_timer.yaml` bestand van je GitHub repository en klik op `Blueprint importeren`. / Paste the URL of this `bewegingslicht_timer.yaml` file from your GitHub repository and click `Import Blueprint`.

2.  **Maak een nieuwe Automatisering / Create a New Automation:**
    * Ga naar `Instellingen` -> `Automatiseringen & Scènes`. / Navigate to `Settings` -> `Automations & Scenes`.
    * Klik op de knop `+ Automatisering maken` (rechtsonder). / Click the `+ Create Automation` button (bottom right).
    * Kies het tabblad `Blueprints`. / Select the `Blueprints` tab.
    * Selecteer de blueprint `Bewegingslicht met Timer (Geavanceerd)`. / Select the `Motion-Activated Lighting with Timer (Advanced)` blueprint.

3.  **Configureer de Automatisering / Configure the Automation:**
    * Vul de vereiste velden in:
        * **Bewegingssensor(en) / Motion Sensor(s):** Selecteer één of meerdere bewegingssensoren die de automatisering moeten triggeren. / Select one or more motion sensors to trigger the automation.
        * **Licht(en) of Scène(s) / Light(s) or Scene(s):** Selecteer de lichten of scènes die je wilt bedienen. / Select the lights or scenes you want to control.
        * **Timer Entiteit / Timer Entity:** Selecteer de `timer` entiteit die je hebt aangemaakt voor deze automatisering. / Select the `timer` entity you created for this automation.
        * **Timer Duur (minuten) / Timer Duration (minutes):** Stel in hoe lang het licht aan moet blijven na de laatste beweging (standaard is 5 minuten). / Set how long the light should stay on after the last motion (default is 5 minutes).
    * Configureer de optionele instellingen indien gewenst:
        * **Starttijd Dagmodus / Day Mode Start Time:** Het tijdstip waarop de dagmodus begint (laat leeg om deze modus over te slaan). / The time when day mode starts (leave empty to skip this mode).
        * **Scène voor Dagmodus / Day Mode Scene:** De scène die geactiveerd moet worden tijdens de dagmodus. / The scene to activate during day mode.
        * **Starttijd Nachtmodus / Night Mode Start Time:** Het tijdstip waarop de nachtmodus begint (laat leeg om deze modus over te slaan). / The time when night mode starts (leave empty to skip this mode).
        * **Scène voor Nachtmodus / Night Mode Scene:** De scène die geactiveerd moet worden tijdens de nachtmodus. / The scene to activate during night mode.
        * **Optionele Conditie(s) / Optional Condition(s):** Voeg extra condities toe indien nodig. / Add any extra conditions if required.
        * **Actie bij Timer Afloop / Action on Timer Expiry:** Kies wat er moet gebeuren als de timer afloopt (`Schakel de lichten uit`, `Dim de lichten naar een bepaald percentage`, of `Activeer een specifieke scène`). / Choose what should happen when the timer expires (`Turn off the lights`, `Dim the lights to a specific percentage`, or `Activate a specific scene`).
        * **Scène bij Timer Afloop (optioneel) / Scene on Timer Expiry (optional):** Indien je `Activeer een specifieke scène` hebt gekozen bij de vorige optie, selecteer hier de gewenste scène. / If you selected `Activate a specific scene` in the previous option, select the desired scene here.
    * Klik op `Opslaan`. / Click `Save`.

## Voorbeelden / Examples
```yaml
# Voorbeeld configuratie via de UI / Example configuration via the UI
Bewegingssensor(en) / Motion Sensor(s): binary_sensor.hallway_motion
Licht(en) of Scène(s) / Light(s) or Scene(s): light.hallway_ceiling
Timer Entiteit / Timer Entity: timer.hallway_light
Timer Duur (minuten) / Timer Duration (minutes): 5
# Uitgebreid voorbeeld met dag/nacht modus en optionele conditie / Advanced example with day/night mode and optional condition
Bewegingssensor(en) / Motion Sensor(s):
  - binary_sensor.living_room_motion_1
  - binary_sensor.living_room_motion_2
Licht(en) of Scène(s) / Light(s) or Scene(s): scene.living_room_ambient
Timer Entiteit / Timer Entity: timer.living_room_light
Starttijd Dagmodus / Day Mode Start Time: 07:00:00
Scène voor Dagmodus / Day Mode Scene: scene.living_room_bright
Starttijd Nachtmodus / Night Mode Start Time: 23:00:00
Nacht Scène / Night Mode Scene: scene.living_room_nightlight
Timer Duur (minuten) / Timer Duration (minutes): 15
Optionele Conditie(s) / Optional Condition(s):
  - platform: device
    device_id: <YOUR_THERMOSTAT_DEVICE_ID>
    domain: climate
    entity_id: climate.living_room_thermostat
    type: is_hvac_mode
    hvac_mode: "heat"
Actie bij Timer Afloop / Action on Timer Expiry: dim
```

## Bekende Problemen / Known Issues
NOT WORKING, work in progress !

