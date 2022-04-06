---
id: dev-guide-configuration
title: Configuration
---

## API

:::note NOTE
Options marked with ***** are not overwritable through `configOverwrite`
:::

### apiLogLevels

type: `Array`

Logs that should go be passed through the 'log' event if a handler is defined for it

Default: **unset**

```javascript
apiLogLevels: ['warn', 'log', 'error', 'info', 'debug']
```

### buttonsWithNotifyClick

type: `Array`

Toolbar buttons which have their click/tap event exposed through the API on
`toolbarButtonClicked`. Passing a string for the button key will
prevent execution of the click/tap routine; passing an object with `key` and
`preventExecution` flag on false will not prevent execution of the click/tap
routine. Below array with mixed mode for passing the buttons.

Default: **unset**

```javascript
buttonsWithNotifyClick: [
    'camera',
    {
        key: 'chat',
        preventExecution: false
    },
    {
        key: 'closedcaptions',
        preventExecution: true
    },
    'desktop',
    'download',
    'embedmeeting',
    'etherpad',
    'feedback',
    'filmstrip',
    'fullscreen',
    'hangup',
    'help',
    {
        key: 'invite',
        preventExecution: false
    },
    'livestreaming',
    'microphone',
    'mute-everyone',
    'mute-video-everyone',
    'participants-pane',
    'profile',
    {
        key: 'raisehand',
        preventExecution: true
    },
    'recording',
    'security',
    'select-background',
    'settings',
    'shareaudio',
    'sharedvideo',
    'shortcuts',
    'stats',
    'tileview',
    'toggle-camera',
    'videoquality',
    // The add passcode button from the security dialog.
    {
        key: 'add-passcode',
        preventExecution: false
    },
    '__end'
]
```

### mouseMoveCallbackInterval

type: `Number`

Default interval (milliseconds) for triggering `mouseMoved` iframe API event.

Default: `1000`

```javascript
mouseMoveCallbackInterval: 1000
```

### useHostPageLocalStorage

type: `Boolean`

This property is related to the use case when jitsi-meet is used via the IFrame API. When the property is true
jitsi-meet will use the local storage of the host page instead of its own. This option is useful if the browser
is not persisting the local storage inside the iframe.

Default: **unset**

```javascript
useHostPageLocalStorage: true
```

## Audio

### audioLevelsInterval

type: `Number`

The interval (milliseconds) at which the audio levels are calculated.

Default: `200`

```javascript
audioLevelsInterval: 200
```

### audioQuality

type: `Object`

Specify audio quality stereo and opusMaxAverageBitrate values in order to enable HD audio.
Beware, by doing so, you are disabling echo cancellation, noise suppression and AGC.

Default: **unset**

```javascript
audioQuality: {
    stereo: false,
    opusMaxAverageBitrate: null // Value to fit the 6000 to 510000 range.
}
```

### disableAudioLevels

type: `Boolean`

Disable measuring of audio levels.

Default: `false`

```javascript
disableAudioLevels: false
```

### disabledSounds

type: `Array`

The sounds passed in this array will be disabled.

Default: **unset**

```javascript
disabledSounds: [
    // 'ASKED_TO_UNMUTE_SOUND'
    // 'E2EE_OFF_SOUND'
    // 'E2EE_ON_SOUND'
    // 'INCOMING_MSG_SOUND'
    // 'KNOCKING_PARTICIPANT_SOUND'
    // 'LIVE_STREAMING_OFF_SOUND'
    // 'LIVE_STREAMING_ON_SOUND'
    // 'NO_AUDIO_SIGNAL_SOUND'
    // 'NOISY_AUDIO_INPUT_SOUND'
    // 'OUTGOING_CALL_EXPIRED_SOUND'
    // 'OUTGOING_CALL_REJECTED_SOUND'
    // 'OUTGOING_CALL_RINGING_SOUND'
    // 'OUTGOING_CALL_START_SOUND'
    // 'PARTICIPANT_JOINED_SOUND'
    // 'PARTICIPANT_LEFT_SOUND'
    // 'RAISE_HAND_SOUND'
    // 'REACTION_SOUND'
    // 'RECORDING_OFF_SOUND'
    // 'RECORDING_ON_SOUND'
    // 'TALK_WHILE_MUTED_SOUND'
]
```

### enableNoAudioDetection

type: `Boolean`

Enabling this will run the lib-jitsi-meet no audio detection module which
will notify the user if the current selected microphone has no audio
input and will suggest another valid device if one is present.

Default: `true`

```javascript
enableNoAudioDetection: true
```

### enableNoisyMicDetection

type: `Boolean`

Enabling this will run the lib-jitsi-meet noise detection module which will
notify the user if there is noise, other than voice, coming from the current
selected microphone. The purpose it to let the user know that the input could
be potentially unpleasant for other meeting participants.

Default: `true`

```javascript
enableNoisyMicDetection: true
```

### startAudioMuted

type: `Number`

Every participant after the Nth will start audio muted.

Default: **unset**

```javascript
startAudioMuted: 10
```

### startAudioOnly

type: `Boolean`

Start the conference in audio only mode (no video is being received nor sent).

Default: **unset**

```javascript
startAudioOnly: false
```

### startSilent

type: `Boolean`

Enabling it (with #params) will disable local audio output of remote
participants and to enable it back a reload is needed.

Default: **unset**

```javascript
startSilent: false
```

### startWithAudioMuted

type: `Boolean`

Start calls with audio muted. This option is only applied locally.

Default: **unset**

```javascript
startWithAudioMuted: false
```

## Callstats

### callStatsConfigParams

type: `Object`

The callstats initialize config params as described in the API:
https://docs.callstats.io/docs/javascript#callstatsinitialize-with-app-secret

```javascript
callStatsConfigParams: {
    disableBeforeUnloadHandler: true, // disables callstats.js's window.onbeforeunload parameter.
    applicationVersion: "app_version", // Application version specified by the developer.
    disablePrecalltest: true, // disables the pre-call test, it is enabled by default.
    siteID: "siteID", // The name/ID of the site/campus from where the call/pre-call test is made.
    additionalIDs: { // additionalIDs object, contains application related IDs.
        customerID: "Customer Identifier. Example, walmart.",
        tenantID: "Tenant Identifier. Example, monster.",
        productName: "Product Name. Example, Jitsi.",
        meetingsName: "Meeting Name. Example, Jitsi loves callstats.",
        serverName: "Server/MiddleBox Name. Example, jvb-prod-us-east-mlkncws12.",
        pbxID: "PBX Identifier. Example, walmart.",
        pbxExtensionID: "PBX Extension Identifier. Example, 5625.",
        fqExtensionID: "Fully qualified Extension Identifier. Example, +71 (US) +5625.",
        sessionID: "Session Identifier. Example, session-12-34"
    },
    collectLegacyStats: true, //enables the collection of legacy stats in chrome browser
    collectIP: true //enables the collection localIP address
}
```

### callStatsID

type: `String`

You must provide the Application ID to enable sending statistics to callstats.io

```javascript
callStatsID: 'my-callstats-app-id'
```

### callStatsSecret

type: `String`

You must provide the Secret to enable sending statistics to callstats.io

```javascript
callStatsSecret: 'my-callstats-secret'
```

### enableDisplayNameInStats

type: `Boolean`

Enables sending participants' display names to callstats.

```javascript
enableDisplayNameInStats: false
```

### enableEmailInStats

type: `Boolean`

Enables sending participants' emails (if available) to callstats and other analytics

```javascript
enableEmailInStats: false
```

### feedbackPercentage

type: `Number`

Controls the percentage of automatic feedback shown to participants when callstats is enabled.
The default value is 100%. If set to 0, no automatic feedback will be requested

```javascript
feedbackPercentage: 100
```
