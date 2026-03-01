# Learning: MQTT Real-time Multiplayer Implementation (2026-03-01)

## Context
Built a real-time racing game (`race.html`) where players compete by tapping the Space-bar. Synchronized states across multiple clients using a public MQTT broker.

## Patterns Discovered
1. **MQTT Retain for Persistence**:
   - Used the `retain: true` flag on the `.../hof` topic to store the *last winner* globally. This acts as a serverless database for high scores.
2. **Heartbeat & Will Message**:
   - Implemented a "Will" message to handle unexpected disconnects.
   - Used a `setInterval` heartbeat to broadcast local state every 200ms.
   - Client-side cleanup for players whose timestamp exceeds 5 seconds (stale check).
3. **Collisionless State Topics**:
   - Each player publishes to a unique topic `${BASE_TOPIC}/state/${myId}` to avoid overwriting others.
   - Subscribers use a wildcard `${BASE_TOPIC}/state/+` to track everyone.

## Code Snippet (State Management)
```javascript
function publishState() {
    client.publish(`${BASE_TOPIC}/state/${myId}`, JSON.stringify({
        id: myId, name: myName, avatar: myAvatar, progress: progress, ts: Date.now()
    }));
}
```

## Resilience
The system handles latency gracefully by using a 5-second timeout for remote players, ensuring the track doesn't get cluttered with "ghost" nodes.
