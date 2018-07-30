# Waveform wrapped when triggered externally

This problem appears for Tektronix AWG5208 with `6.0.0242.0`
 firmware version (might be also for all `6.0.*` versions).

The problem is that when a waveform is triggered externally, after a number 
of external triggers, it gets wrapped around (i.e. its starting point drifts).
In other words, it is played not at its start but at a point a bit further 
along. Moreover, the point from which the waveform is played is slowly shifting.
 
Newer versions of the firmware, at least `6.1.0054.0` (and presumably all 
`6.1.*` versions), do not exhibit this problem. Thus, in case AWG5208 
waveforms need to be triggered externally, then the AWG has to have the 
firmware with the abovementioned version installed.  
 
For more information, refer to the report in `report.rst`.
