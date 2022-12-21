## Simulated issues for a better understanding....
### Quiz 1:
Tag: q1 <br>
Fault reported: <br>
After some configuration changes, <br>
rooms can be successfully booked via room-mgmt API with following:
curl -v --request POST 'http://localhost:7070/rooms' 
--header 'Content-Type: application/json' 
--data-raw '{
    "requestor": "10206739",
    "name": "test-room-ABC",
    "startTime": "2021-11-27T00:00:00+08:00",
    "endTime": "2023-09-07T14:00:00Z"
}'

But partcipants cannot join the room sessions with following error:
###### ERROR default: [room-recorder_session.go:214] [recorder.(*RoomRecorderSession).onRoomError] onRoomError rpc error: code = Internal desc = RoomId '977558b3-016b-4731-a50f-6723a1802145' not found in database  <br>
### Quiz 2:
Tag: q2 <br>
Fault reported: <br>
After some configuration changes, <br>
rooms can be successfully booked via room-mgmt API with following:
curl -v --request POST 'http://localhost:7070/rooms' 
--header 'Content-Type: application/json' 
--data-raw '{
    "requestor": "10206739",
    "name": "test-room-ABC",
    "startTime": "2021-11-27T00:00:00+08:00",
    "endTime": "2023-09-07T14:00:00Z",
    "allowedUserId": [
        "10206739",
        "10208888"
    ]
}'
But room-recorder cannot join the room sessions with following error:
###### ERROR default: [room-recorder_session.go:214] [recorder.(*RoomRecorderSession).onRoomError] onRoomError rpc error: code = Internal desc = UserId 'aeae639f-7a3a-4bcb-ba18-6986cf48e2f2MtyfwSaP0bN61Z1c' userName '' is denied in RoomId '3941296d-57d7-40b5-8dcf-cf8afca7405c'
