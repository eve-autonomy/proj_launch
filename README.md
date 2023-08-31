# Project Launch: Additional nodes for the "cargo transportation" project

## Overview
This package manages in-vehicle nodes especially for state management, HMI control, delivery reservation, and Vehicle to Infrastructure (V2I) connection.

## Node Graph
![node graph](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/eve-autonomy/proj_launch/main/docs/node_graph.pu)<br>
Note: This package manages the red colored nodes.
<details><summary>List of managing repositories</summary><div>

- Nodes
  - State management:
    - [/autoware_state_machine](https://github.com/eve-autonomy/autoware_state_machine)
    - [/engage_service](https://github.com/tier4/engage_service)
  - HMI control:
    - Sound control:
      - [/ad_sound_manager](https://github.com/eve-autonomy/ad_sound_manager)
      - /sound_bgm[/audio_driver](https://github.com/eve-autonomy/audio_driver)
      - /sound_voice_alarm[/audio_driver](https://github.com/eve-autonomy/audio_driver)
    - Lamp control:
      - [/ad_status_lamp_manager](https://github.com/eve-autonomy/ad_status_lamp_manager)
      - [/delivery_reservation_lamp_manager](https://github.com/eve-autonomy/delivery_reservation_lamp_manager)
      - [/warning_lamp_manager](https://github.com/eve-autonomy/warning_lamp_manager)
    - Button control:
      - [/button_manager](https://github.com/eve-autonomy/button_manager)
      - [dio_ros_driver](https://github.com/tier4/dio_ros_driver)
      - [/engage_srv_converter](https://github.com/eve-autonomy/engage_srv_converter)
      - [/button_output_selector](https://github.com/eve-autonomy/button_output_selector)
  - Reserved-delivery connection:
    - [/go_interface](https://github.com/eve-autonomy/go_interface)
  - V2I connection:
    - [/v2i_interface](https://github.com/eve-autonomy/v2i_interface)
  - Shutdown process management:
    - [/shutdown_manager](https://github.com/eve-autonomy/shutdown_manager)
  - Cargo Loading management:
    - [/cargo_loading_service](https://github.com/eve-autonomy/cargo_loading_service)
    - [diagnostics](https://github.com/tier4/diagnostics)
    - [interface_utils](https://github.com/tier4/interface_utils)
  - Parking task management:
    - [/in_parking_task_manager](https://github.com/tier4/in_parking_task_manager)
    - [/lanelet2_map_parse_service](https://github.com/tier4/lanelet2_map_parse_service)
    
- Message definition
  - State management:
    - [autoware_state_machine_msgs](https://github.com/eve-autonomy/autoware_state_machine_msgs)
  - HMI control:
    - Sound control:
      - [audio_driver_msgs](https://github.com/eve-autonomy/audio_driver_msgs)
  - Reserved-delivery connection:
    - [go_interface](https://github.com/eve-autonomy/go_interface)
  - Shutdown process management:
    - [shutdown_manager_msgs](https://github.com/eve-autonomy/shutdown_manager_msgs)
  - Parking task management:
    - [in_parking_msgs](https://github.com/tier4/in_parking_msgs)
    - [lanelet2_parse_msgs](https://github.com/tier4/lanelet2_parse_msgs)
    - [tier4_autoware_msgs](https://github.com/tier4/tier4_autoware_msgs)
  - V2I connection:
    - [v2i_interface_msgs](https://github.com/eve-autonomy/v2i_interface_msgs)

- Parameters
  - Reserved-delivery connection:
    - [go_interface_params.default](https://github.com/eve-autonomy/go_interface_params.default)
  - V2I connection:
    - [v2i_interface_params.default](https://github.com/eve-autonomy/v2i_interface_params.default)

- Dataset
  - HMI control:
    - Sound control:
      - [ad_sound.default](https://github.com/eve-autonomy/ad_sound.default)

- Library
 - [/autoware_common](https://github.com/autowarefoundation/autoware_common) 
 

</div></details>

## Environment variables

|Name|Description|
|:---|:----------|
|OPR_MODE_V2I|Select one of the operation modes to the v2i connection `/v2i_interface` from the followings; <br>  `product`, `local_test` <br> This parameter works as [`operation_mode`](https://github.com/eve-autonomy/v2i_interface#launch-arguments).|
|OPR_MODE_DELY_RSV|Select one of the operation modes to the delivery reserve application `/go_interface`  from the followings; <br>  `product`, `server_test`, `local_test`, `not_use` <br> This parameter works as [`operation_mode`](https://github.com/eve-autonomy/go_interface#launch-arguments).|
|ACCESS_TOKEN_DELY_RSV|Specify an access token of the reserve application `/go_interface`. This setting is reflected in the value of [`access_token`](https://github.com/eve-autonomy/go_interface#launch-arguments) in go_interface.|
|AD_SOUND_LANGUAGE|Select a sound language in `ad_sound_manager`. This parameter is same to directory name of the node and works as [`lang`](https://github.com/eve-autonomy/ad_sound_manager#launch-arguments) in ad_sound_manager.|

## Launch arguments

|Name|Description|
|:---|:----------|
|use_overridable_vehicle|If autonomous driving vehicle has a function of override, set this parameter as `TRUE`. Otherwise set as `FALSE`.|
|operation_mode_v2i_infra|Select the operation mode of the V2I interface from the followings; <br>`product`, `local_test` <br> This parameter works as [`operation_mode`](https://github.com/eve-autonomy/v2i_interface#launch-arguments).|
|operation_mode_delivery_reservation|Command line of the launcher for overriding `OPR_MODE_DELY_RSV`[^1].|
|access_token_delivery_reservation|Command line of the launcher for overriding `ACCESS_TOKEN_DELY_RSV`[^1].|
|ad_sound_language|Command line of the launcher for overriding `AD_SOUND_LANGUAGE`[^1].|

[^1]: When an arbitrary value is set, these environment variables are ignored.

