# jukerstone-react-native

Licensed music playback by ISRC, powered by Spins™.

This React Native SDK gives you playback control over pre-cleared music videos using ISRCs — with full queueing, buffering, and cross-platform support.

📍 Unlike the iOS SDK, this version **supports queuing multiple tracks** for seamless transitions.

---

## 🔗 Live Docs  
https://www.jukerstone.com/sdk/#music-videos

---

## 🧪 5 Free Spins for Testing

Every developer account includes **5 free Spins** to try playback.

### Sample ISRCs:
```
USUM72105973
USQX91402597
USUM70846400
USUYG1001593
FRX202363539
```

---

## ⚙️ Setup

1. Install via NPM (coming soon)
2. Wrap your app with the SDK Provider:

```tsx
import { JukerstoneProvider } from 'jukerstone-react-native';

export default function App() {
  return (
    <JukerstoneProvider>
      <YourApp />
    </JukerstoneProvider>
  );
}
```

---

## ▶️ Minimal Playback Example

```tsx
import React from 'react';
import { View, Button } from 'react-native';
import { useJukerstone } from 'jukerstone-react-native';

export default function MusicPlayer() {
  const {
    queue,
    handlePlayNext,
    handleStop,
    isPaused,
    setIsPaused,
    handleSeek,
  } = useJukerstone();

  return (
    <View>
      <Button title="Play Track" onPress={() => queue(['USUM72105973'])} />
      <Button title="Play Next" onPress={handlePlayNext} />
      <Button title="Stop" onPress={handleStop} />
      <Button
        title={isPaused ? 'Resume' : 'Pause'}
        onPress={() => setIsPaused(!isPaused)}
      />
      <Button title="Seek to 60s" onPress={() => handleSeek(60)} />
    </View>
  );
}
```

---

## 📦 Core Hooks

Available from `useJukerstone()`:

- `queue` — add ISRCs to playback
- `handlePlayNext` — go to next
- `handleStop` — stop current playback
- `isPaused`, `setIsPaused` — control playback state
- `handleSeek` — seek by seconds
- `currentTrack` — metadata & progress
- `repeatOptions`, `setRepeatOptions`
- `isPrimaryPlayer` — active player state
- `buffer1`, `buffer2` — internal WebView buffers

…and more for advanced usage: buffering, preload keys, PiP, etc.

---

## 🎧 Playback Events

The SDK internally emits key events like:

- `videoCurrentTime` – current progress
- `videoEnded` – when track finishes

You can optionally poll or track `currentTrack.progress` for deeper integrations.

---

## 🆘 Support

📩 support@jukerstone.com  
📚 https://www.jukerstone.com/sdk/#music-videos

---

Built for developers. Powered by Spins™.
