[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

# Blauberg EcoVent VENTO Expert A50/80/100 V.2 Fans
Home Assistant Integration. Integration for newest Fans with api version 2


# Tested on:
* Blauberg VENTO Expert A50-1 W V.2

# Currently supported:
* UI integration setup
* turn_on/turn_off
* Preset modes:
  - low
  - medium
  - high
  - manual
* In manual mode speed percentage
* Oscillating
  - When on, Fans are in 'heat_recovery' airflow
* Direction
  - "forward" means 'ventilation' airflow
  - "reverse" means 'air_supply' airflow

# Changelog
version 0.0.5:
* Added sensors:
  - Humidity
  - Fan1 speed
  - Fan2 speed
  - Airflow

* Changed
  - Update method to DataUpdateCoordinator for reduced request to FAN device

version 0.1.0:
* Added sensors:
  - battery_voltage
  - timer_counter
  - humidity_treshold
  - filter_timer_countdown
  - boost_time
  - machine_hours
  - analogV
  - analogV_treshold

All sensors are categorised and some are disabled by default.

version 0.2.0:
* Added binary sensors:
  - boost_status
  - timer_mode
  - humidity_sensor_state
  - relay_sensor_state
  - relay_status
  - filter_replacement_status
  - alarm_status
  - cloud_server_state
  - humidity_status
  - analogV_status

All sensors are categorised and some are disabled by default.

* Changed:
  - Removed default IP address from config input field Host
  - Added some icon defintions to sensors
  - Battery percent caluclation

version 0.2.0:
* Added services
  - filter_timer_reset (Reset air filter timer)
  - reset_alarms (Reset fan Vento alarms)
* Changed:
  - From binary sensor to switch:
    - humidity_sensor_state
    - relay_sensor_state
    - analogV_sensor_state

version 0.4.0
* Added broadcast devices search
  - hack, that searches on network, if string: <broadcast> is entered
    instead of IP address
  - this is not yer proper HomaAssistant Auto Discovery, but it seems to
    work on my network

version 0.5.0
* Mainly fixes from autmated checks and hopefuly some latency improvements
  - Removed await coordinator in turn_on/turn_off and other interactive
    functions
  - Some cleanup in config_flow
  - Removed deprecated set_speed functions
  - Fix error if _battery_voltage is None

version 0.6.0
* Timeout Loop bailout

version 0.7.0
* Fix manifest, to require correct pyEcovent version (0.9.14)

version 0.8.0
* Removed calling blocking sleep in event loop

version 0.9.0
* Cleanup some definitions for HA checks

version 0.9.1
* replaced hass.config_entries.async_setup_platforms with await hass.config_entries.async_forward_entry_setups
* thanks to @berndulum for issue report

version 0.9.2
* fix name of sensor leaking to device name (hopefuly)

version 0.9.3
* bump requirements to pyEcoventV2==0.9.16 (fixed boost_status reading)

version 0.9.5
* Merged pull request for file "protocol.md" by @Styx85.

version 0.9.6
* Fix: Humidy Threshold creates errors trouble in newest HA #21
* humidity_treshold, analogV_treshold, boost_timer changed from sensor to number. Now they can be configured via HomeAssistant.

Version 0.9.7
* Updatet README.md

Version 0.9.8
* Fix number entities names.

Version 0.9.9
* more  entities names fixes.

Version 1.0.0
* some more name fixes
* fix code to be more compliant with latest HA
* some code cleanup

Version 1.0.1
* Values for humidity_threshold, analogV_threshold and boost ime read from device on initialization.

Version 1.0.2
* Fix for issue #25 VentoExpertFan does not set FanEntityFeature.TURN_OFF but implements the thurn_off method

Version 1.0.3
* Merge pull request #28 from SantaFox/main: Amended some sensors for better automations

Version 1.0.4

Version 1.0.5
* Bump pyEcoventV2 requirements to 0.9.19

Version 1.0.6
* Bump pyEcoventV2 requirements to 0.9.21, trying to resolve different lengths of returned value for filter_timer_counter

Version 1.0.7 / 1.0.8
* Bump pyyecoventv2 requirements to 0.9.22, still trying to fix 4 byte return of filter_timer_counter function

Version 1.0.9
* Bump pyyecoventv2 requirements to 0.9.23, remove beeper gueswork

