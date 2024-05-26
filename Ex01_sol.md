## Exercise 01

**States**

light off

manual mode

motion detection mode - no motion detected

motion detection mode - motion detected

**Events**

ON_pressed

OFF_pressed

MOT_pressed

motionm_detected

time_tik_30_s

**Variables**

brightness

**Pseudo code**

we have the enums that represent the states and events (could also be represented by constants).
```c
void handle_event(state_t *state, event_t event){
  switch(*state){
    case light_off:
      switch(event){
        case ON_pressed:
          brightness=1
          turn light on with brightness  
          *state = manual_mode:
          break;
        case MOT_pressed:
          brightness=0
          *state = motion_detection_mode_no_motion_detected:
          break;
          
      }
      break;
    case manual_mode:
      switch(event){
        case ON_pressed:
          brightness=brightness%3 + 1
          set light brightness   
          *state = manual_mode:
          break;
        case MOT_pressed:
          brightness=0
          *state = motion_detection_mode_no_motion_detected:
          break;
        case OFF_pressed:
          brightness=0
          *state = light_off:
          break;        
      }
      break;
    case motion_detection_mode_no_motion_detected:
      switch(event){
        case motionm_detected:
          brightness=3
          set light brightness   
          *state = motion_detection_mode_motion_detected;
          break;
        case OFF_pressed:
          brightness=0
          *state = light_off:
          break;          
        case ON_pressed:
          brightness=1
          set light brightness   
          *state = manual_mode:
          break;          
      }
      break;
    case motion_detection_mode_motion_detected:
      switch(event){
        case time_tik_30_s:
          brightness=0
          set light brightness 
          *state = motion_detection_mode_no_motion_detected:
          break;
        case motionm_detected:
          brightness=3
          set light brightness   
          *state = motion_detection_mode_motion_detected;
          break;
        case OFF_pressed:
          brightness=0
          *state = light_off:
          break;          
        case ON_pressed:
          brightness=1
          set light brightness   
          *state = manual_mode:
          break;          
      }
      break;
  }
}
```

