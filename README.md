# AWS DeepRacer Free Student Workshop: Run faster by using your custom waypoints
# Reward Function Template for waypoints

```python
def reward_function(params):

    center_variance = params["distance_from_center"] / params["track_width"]
    #racing line
    left_lane = [38,39,40,41,42,43,49,50,51,52,53,102,103,104,105,106,107,108,117,118,119,120,121,122,123,]#Fill in the waypoints
    
    center_lane = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,44,45,46,47,48,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,81,95,109,110,111,112,113,114,115,116,125,126]#Fill in the waypoints
    
    right_lane = [85,86,87,88,89,90,91]#Fill in the waypoints
    
    #Speed
    fast = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,81,85,86,87,88,89,90,91,95,111,112,113,114,115,116,124,125,126,1271.5]#Fill in the waypoints, 4m/s
    medium= [33,35,44,45,46,47,102,103,104,109,110,117,118,119,120,121,122,123]#Fill in the waypoints, 2.5m/s
    slow = [38,39,40,41,42,43,48,49,50,51,52,53,106,107,108]#Fill in the waypoints, 1.5m/s
    
    reward = 21

    if params["all_wheels_on_track"]:
        reward += 10
    else:
        reward -= 10

    if params["closest_waypoints"][1] in left_lane and params["is_left_of_center"]:
        reward += 10
    elif params["closest_waypoints"][1] in right_lane and not params["is_left_of_center"]:
        reward += 10
    elif params["closest_waypoints"][1] in center_lane and center_variance < 0.4:
        reward += 10
    else:
        reward -= 10
    if params["closest_waypoints"][1] in fast:
        if params["speed"] == 4 :
            reward += 10
        else:
            reward -= 10
    elif params["closest_waypoints"][1] in medium:
        if params["speed"] == 2.5 :
            reward += 10
        else:
            reward -= 10
    elif params["closest_waypoints"][1] in slow:
        if params["speed"] == 1.5 :
            reward += 10
        else:
            reward -= 10
        
    
    return float(reward)
```
## Wokrshop Guideline
https://www.linkedin.com/pulse/aws-deepracer-free-student-workshop-run-faster-using-your-cheuk-lam/?published=t
## Demo Video
https://youtu.be/__NjsBY2TS0
## Other Workshop
[AWS Educate Classroom for a free AWS DeepRacer Student Workshop](https://www.linkedin.com/pulse/aws-educate-classroom-free-deepracer-student-workshop-yuen-oscar/?trackingId=Ug9v8CodQdG7MXETAri5Ww%3D%3D)

## Credit
https://github.com/aws-deepracer-community/deepracer-analysis

https://github.com/aws-deepracer-community/deepracer-race-data/tree/main/raw_data/tracks/npy
