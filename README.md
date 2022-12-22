## Simulated issues for a better understanding....
### Quiz 1:
Tag: q1 <br>
Fault reported: <br>
After some configuration changes, rooms can be successfully booked via room-mgmt API. <br>
But partcipants cannot join the room sessions with following errors:
###### ERROR default: [room-recorder_session.go:214] [recorder.(*RoomRecorderSession).onRoomError] onRoomError rpc error: code = Internal desc = RoomId '977558b3-016b-4731-a50f-6723a1802145' not found in database

### Quiz 2:
Tag: q2 <br>
Fault reported: <br>
After some configuration changes, rooms can be successfully booked via room-mgmt API with following: <br>
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
}'  <br>
But room-recorder cannot join the room sessions with following errors:
###### ERROR default: [room-recorder_session.go:214] [recorder.(*RoomRecorderSession).onRoomError] onRoomError rpc error: code = Internal desc = UserId 'aeae639f-7a3a-4bcb-ba18-6986cf48e2f2MtyfwSaP0bN61Z1c' userName '' is denied in RoomId '3941296d-57d7-40b5-8dcf-cf8afca7405c'

### Quiz 3:
Tag: q3 <br>
Fault reported: <br>
After some configuration changes, room-playback always fail with following errors:
###### ERROR default: [room-playback_peer.go:219] [playback.(*PlaybackPeer).preparePlaybackPeer] could not process download: The specified key does not exist. 
###### ERROR default: [room-playback_peer.go:258] [playback.(*PlaybackPeer).preparePlaybackPeer] preparePlaybackPeer peerId '189fffa7-bbc0-4fb8-9ab0-cd9d4967f3cf' found no usable tracks 

### Quiz 4:
Tag: q4 <br>
Fault reported: <br>
After some code changes, rooms can be successfully booked via room-mgmt API with following: <br>
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
}'  <br>
But despite setting the "allowedUserId" to be a list of restricted usersIds, anybody can still join the room, with no error messages in the logs

### Quiz 5:
Tag: q5 <br>
Fault reported: <br>
After some code changes, rooms can be successfully booked via room-mgmt API with following: <br>
curl -v --request POST 'http://localhost:7070/rooms' 
--header 'Content-Type: application/json' 
--data-raw '{
    "requestor": "10206739",
    "name": "test-room-ABC",
    "startTime": "2021-11-27T00:00:00+08:00",
    "endTime": "2023-09-07T14:00:00Z"
}'  <br>
But partcipants cannot join the room sessions with following errors:
###### ERROR default: [room_signal.go:60] [server.(*RoomSignalService).Signal] Join err: rpc error: code = Internal desc = RoomId '501f6fb3-48b0-4490-9278-d3245c49955a' session not started 

### Quiz 6:
Tag: q6 <br>
Fault reported: <br>
After some code changes, room-playback occasionally fail with following errors:
###### ERROR default: [room-playback_peer.go:219] [playback.(*PlaybackPeer).preparePlaybackPeer] could not process download: The specified key does not exist. 
###### ERROR default: [room-playback_peer.go:258] [playback.(*PlaybackPeer).preparePlaybackPeer] preparePlaybackPeer peerId '189fffa7-bbc0-4fb8-9ab0-cd9d4967f3cf' found no usable tracks 
