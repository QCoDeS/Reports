Waveform wrapped when triggered externally on the AWG5208
=========================================================


Abstract
--------

When a waveform is triggered externally on ``AWG5208`` with firmware version
``6.0.0242.0``, after a number of triggers, it gets wrapped, i.e. it is
played not from its beginning but a bit later. In order to avoid this
problem, just use a newer version of firmware; ``6.1.0054.0`` is confirmed
to not exhibit this problem.


Setup
-----

The basic setup for testing this contains the Tektronix AWG5208, Keysight
Infiniium MSOS254A mixed signal oscilloscope, and Rigol DG1062 signal
generator. First channel of the AWG is connected to the scope, together with
one marker channel. Signal generator is connected to the ``TrigA`` input of
the AWG, and to the scope.

A program was written to upload a simple staircase ramp waveform with triggers
for each step to the first channel of the AWG. The total duration of the
waveform was ~10ms, the number of steps (and triggers) was 10. The waveform
starts in the event of receiving signal from TrigA, which is set to 0V level,
with rising edge, 50 Ohm impedance, and Fast timing. The sample rate was
10 MS/s.

The signal generator was setup to emit a step from -0.5V to +0.5V. Emitting
this signal was commanded from the program.

The flow of the experiment is the following:

- Upload the waveform to AWG
- Set up the signal generator
- Set up the scope to view the output of AWG together with the signal emitted
  from the signal generator
- Press "Play" on AWG so that the waveform is ready to be played
- Periodically send commands to the signal generator to emit the trigger
  signal, and observe the signals that AWG emits on the scope


Results
-------

The observed behavior is the following. After a number of times the waveform
is played (~20), the first trigger from the waveform suddenly disappears, and
appears at the end of the waveform. Together with this, the observer also
notices that the not only the first trigger got moved to the end of the
waveform, but the whole staircase ramp pattern got shifted. After more times
of playing the waveform, the "drifting" continues, and the two of the first
trigger signals from the marker channel are now at the end of the waveform.

Note that neither sample rate, nor duration of the waveform matter. While
preserving the shape of the waveform and increasing the sample rate to
maximum, the number of times the waveform needed to be played, in order for
the drift/wrapping to be observed, increased. Nevertheless, when the number
of steps within the staircase ramp pattern has been increased, the
drift/wrapping started to appear earlier again.


Solution
--------

The solution was found to be just using a later version of the firmware. In
particular, the same measurement has been performed with AWG5208 with
``6.1.0054.0`` firmware version, and the drift/wrapping behavior has not been
observed.


Conclusion
-----------

In case an experiment is being set up where waveforms from AWG5208
need to be triggered externally, then the used AWG5208 has to have a firmware
with the version that is at least ``6.1.0054.0``.
