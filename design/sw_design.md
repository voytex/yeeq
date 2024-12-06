<style>
body { counter-reset: h1counter h2counter h3counter h4counter h5counter h6counter; }

h1 { counter-reset: h2counter; }
h2 { counter-reset: h3counter; }
h3 { counter-reset: h4counter; }
h4 { counter-reset: h5counter; }
h5 { counter-reset: h6counter; }
h6 {}

h2:before {
    counter-increment: h2counter;
    content: counter(h2counter) ".\0000a0\0000a0";
}

h3:before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) ".\0000a0\0000a0";
}

h4:before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) ".\0000a0\0000a0";
}

h5:before {
    counter-increment: h5counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) "." counter(h5counter) ".\0000a0\0000a0";
}

h6:before {
    counter-increment: h6counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) "." counter(h5counter) "." counter(h6counter) ".\0000a0\0000a0";
}
</style>
## High Level Requirements

### GUI requirements
1. Window shall be divided into two halves. One for **DAW status**, the other for **Bulbs status**.

#### DAW status
1. DAW status shall contain control field for MIDI messages signaling recording start and stop
1. DAW status shall contain control field for MIDI messages signaling playing start and stop
1. DAW status shall contain CUE status (e.g. REC/PLAY) indication
> Future version might contain also a choice for different DAW, if signaling via MIDI messages would not sufficient. 

#### Bulbs status
1. Bulb status shall contain a button for refreshing states of all bulbs in LAN
1. Bulb status shall contain a table with reachable bulbs
1. Bulb status shall contain controls for setting the bulb states when following events have been received from DAW:
   - recording start
   - recording stop
   - (optional) playing start
   - (optional) playing stop

## Low Level Requirements
### `refresh()`
- Refreshes table of reachable bulbs
### `