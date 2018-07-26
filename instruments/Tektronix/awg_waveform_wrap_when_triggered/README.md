# Waveform wrapped when triggered externally

This problem appears for Tektronix AWG5208 with `6.0.0242.0`
 firmware version (might be also for all `6.0.*` versions).

The problem is that when a waveform is triggered externally, after a number 
of external triggers, it gets wrapped around. In other words, it is played 
not at its start but at a point a bit further along. Moreover, the point from
 which the waveform is played is slowly shifting.
 
Newer versions of the firmware, at least `6.1.0054.0` (and presumably all 
`6.1.*` versions), do not exhibit this problem. 
 
For more information, refer to the report in `report.rst`.
