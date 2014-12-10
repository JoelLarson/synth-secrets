# SYNTH SECRETS  
_Original article: [http://www.soundonsound.com/sos/Oct01/articles/synthsecrets30.asp][0]_

**Having proved that subtractive synthesis of an acoustic guitar is completely impractical, **Gordon Reid**tries his hand at the electric variety, and deconstructs some past attempts to emulate the sound via analogue means. This is the 30th article in a 63-part series. Read [all parts][1].**

![](http://media.soundonsound.com/sos/oct01/images/synthparkermidifly.gif)

For the past two months, I've used about 7000 words and 40 diagrams to explain why it's not practical to emulate guitar sounds using traditional analogue synthesis. So why does every synthesizer patch book include voices with names such as 'Jazz Guitar', 'Funky Wah-Wah Guitar', 'E-Guitar', or something similar? The answer to this lies in the nature of the guitar that the patch is attempting to emulate.

In the last two parts of this series, I restricted my analysis to the qualities of the acoustic guitar, with all of its resonant surfaces and complex enclosed spaces. But let's ask what happens when we take the six primary oscillators of the acoustic guitar (the strings) and attach them to a _solid_ body. What we now have is a guitar that comprises six strings, a neck, some form of tuning mechanism, and a wooden plank that acts as its resonator. We can add devices such as electromagnetic pickups, volume and tone circuitry, a tremolo system, and even digital signal processing technology -- but none of these affect the basic sound produced by the instrument. Indeed, until you plug this 'electric' guitar into an amplifier and speaker, the vibrations of the strings themselves dominate its sound. Sure, the weight of the body and the quality of the material from which it is constructed will have a subtle effect, but there is no acoustic cavity and no soundboard to amplify and modify that sound.

Extending this line of reasoning, we could hypothesise (correctly) that the traditional guitar shape is no longer relevant to the sound of the electric guitar. It is for this reason that the glam-rock bands of the '70s could play guitars shaped like stars, the letter 'V', that were circular, or even carved in the shape of Africa (this tells us why they _could_, but gives us no inkling about why they _did_. I guess you just had to be there).

But why stop there? Since the electric guitar is insensitive to its body shape, it seems reasonable to speculate that it will be similarly indifferent to the material from which the body is made. And, although many guitarists will wax lyrical about their favourite lumps of dead tree, this is not such a stupid idea. There have long been graphite guitars and basses, and I remember wanting an aluminium-necked Kramer in the early '80s.

So, let's ask what this has to do with analogue synthesis. The answer is obvious: none of the guitar patches designed for early analogue synthesizers attempted to produce the complex sound of a nylon-strung, hollow-bodied acoustic instrument. All of them emulate, to a greater or lesser extent, the (hypothetically) simpler sound of the solid-bodied electric guitar.

**The Electric Guitar**

We're going to try to use our knowledge of the electric guitar to simplify -- or, at the very least, make more practical -- the analogue 'model' of the acoustic guitar that concluded last month's Synth Secrets (see Figure 1, opposite).

Starting on the left-hand side of this, we find the slew generator, LFO, VCA and mixer that provide much of the performance capabilities within the patch. Since all six-string guitars are equally capable of slides, bends and vibrato, these modules remain unaffected by the transition from the acoustic to the electric guitar, so we will retain them in the electric guitar patch.

The next element, and the first in the audio signal path, is the oscillator, and we shall leave this where we found it. The output from this passes through the high-frequency equaliser that I introduced to[![](http://media.soundonsound.com/sos/oct01/images/synth1s.gif)][2] model the hardness of the pick, and this too survives the move from an acoustic to an electric guitar patch. So far... so identical.

Next, the audio signal passes through a VCA controlled by an AD contour generator. The loudness and brightness envelopes of an unamplified electric guitar are very different from those of an acoustic guitar but, although the speed and the precise shape of the decay differ, the underlying characteristics remain the same. Therefore, we will also leave this part of the patch untouched.

After this, the audio passes through a complex filter bank that imposes the resonant characteristics of the guitar body upon it. Hang on a moment... haven't I implied that the electric guitar's body is all but irrelevant? Well, yes I have. Nevertheless, although an electric guitar has fewer and less significant resonances (compared with an acoustic guitar) those that survive still play a part in its sound. So, can we dispense with the filter bank? Obviously not.

The output from the filter bank passes along two signal paths. The first of these is the feedback loop that emulates the way in which the body of the acoustic guitar absorbs energy from the vibrating strings and then passes it back in ways that modify their vibrations. Because an electric guitar's body absorbs and radiates little energy in comparison with the acoustic guitar's, it's tempting to suggest that we can dispense with this loop. After all, it would simplify the patch considerably. Unfortunately, we can't do so with a clear conscience. The interactions between the strings and the body are less important, but we would still be removing a part of the model's sound-generation system. 

The second audio path exiting the filter bank passes through a low-pass filter that models the decreasing high-frequency content of the signal as the note decays in time. This too must stay, as must the mixer that combines the sounds produced by the six voices.

We now come to the filter bank that emulates the way in which the sound of the acoustic guitar depends upon the relative positions of the player and listener, and the relative angle at which the player holds the guitar. Clearly, this is not necessary for, or relevant to, our electric guitar patch. However, when you listen to someone playing an electric guitar, you hear an amplified signal through a speaker of some sort. So, while we no longer need the filter bank to model the relative position of the guitar, we now require it to model the complex response and resonances of the reproduction mechanism. Again, the patch should remain unchanged.

The final elements in our synthesized model lie at the top of Figure 1\. These control voltages and physical controllers allow us to play the sound in a realistic fashion and, in an ideal world, we will retain all of them. After all, we still want to imitate all the nuances and performance capabilities of the guitar, whether the amplifier is a hollow body or a bunch of transistors.

So where does that leave us? Surprisingly, it plonks us precisely back where we started. Although the sound of an electric guitar is very different from that of an acoustic guitar, the sound-generation mechanism is fundamentally the same.

**Patch 1 -- The ARP Axxe**

If I follow customary Synth Secrets practice, I should now present a second diagram that depicts the ideal electric guitar patch. At this point in our analysis, however, this would seem to be identical to Figure 1[![](http://media.soundonsound.com/sos/oct01/images/synth_2_5s.gif)][3] and, since I have no wish to be ritually beheaded by _Sound On Sound_'s graphics department for gratuitous over-use of a hideously unwieldy diagram, I'm going to offer you something else. This is the 'Jazz Guitar' patch from the ARP Axxe patch book published by ARP in 1977 or thereabouts (see Figure 2 above).

As you can see, this patch is much simpler than the one depicted in Figure 1\. This is inevitable; the Axxe is far too basic to do more. You can see just how simple it is by comparing the block diagram in Figure 3 (which shows all the elements of the patch) to the 100+ modules in Figure 1... Even ignoring the fact that the Axxe is monophonic, it's a huge difference.

Let's now consider some of the 'Jazz Guitar' modules, starting with the oscillator. There is an immediate surprise here ... contrary to our analysis of the past two months, the patch does not use a sawtooth waveform, but rather utilises a pulse waveform with a duty cycle of about 25 percent. This is really rather clever. The Axxe has no complex filter bank, so there is no way to remove or accentuate narrow bands of frequencies once the oscillator has generated them. Using a narrow pulse introduces some of these holes, albeit in a rather crude way. This is because a 25 percent pulse wave lacks every fourth harmonic. Sure, no guitar body has resonances as evenly spaced as the holes in a pulse wave's harmonic series, so it is -- at best -[![](http://media.soundonsound.com/sos/oct01/images/synth_6s.gif)][4]- a poor approximation. Furthermore, the resonances of the guitar are stationary, whereas the holes in the pulse wave's harmonic structure travel up and down the spectrum as you play up and down the keyboard. Nonetheless, the results are more satisfying than using a sawtooth, and that's what matters. 

Let's now look at the envelope generator. The contour generated by this is applied to both the VCF and of the VCA, thus shaping the note in the way suggested in Figure 1\. However, the ADSR shape is set up rather strangely. I agree that the Attack should be as close to instantaneous as possible, and knowing the time constants of the Axxe's contours, a Decay of '6' or '7' seems reasonable. But what of the Sustain level of '4' or thereabouts? Unlike our analysis of a real guitar's contour (see Figure 4 above) the Axxe contour (shown in Figure 5, right) implies that a jazz guitar will sustain indefinitely if you ask it to do so, which -- in my experience -- is not the case. OK, the guitar could be heavily amplified, and the player could be using acoustic feedback from the speaker to the strings to create indefinite sustain. But since this method of playing is more usually the province of overdriven, jaw-clenching, angst-driven, testosterone-fuelled guitar solos, I still contend that it's wrong for this sound.

Moving on, the Axxe is very limited in terms of performance capabilities, but the patch makes the best of the options available. The original version of the patch suggested that the player use the LFO slider in the oscillator section to add vibrato manually, and the pitch-bend knob to create bends and slides. [![](http://media.soundonsound.com/sos/oct01/images/synth_7s.gif)][5]The version of the Axxe shown in the diagram is significantly more expressive than this, allowing you to use the three pressure-sensitive pads (which were added to later production versions of the synth) to recreate these effects in a far more natural way.

Now, the Axxe is a monophonic synth, so there is no question of it producing strums or chords. Nevertheless, you could be forgiven for expecting satisfying results if you use it to play melodies in a fashion that is sympathetic to the realities of the electric guitar. Unfortunately, you would be wholly wrong to do so. Played dry, this patch sounds like an analogue synth. Played through a clean guitar amp, it sounds like an analogue synth played through a clean guitar amp. Played through a screaming 100W Marshall stack it sounds like... well, an analogue synth pretending to be a guitar playing through a screaming Marshall stack. The only way to get this patch to sound anything like a guitar is to distort it so much that the overriding factor is the distortion itself, not the sound produced by the synth.

**Patch 2 -- The Roland SH101**

Of course, it may be that the Axxe is unable to create a convincing guitar sound, so let's try another instrument. Figure 6 (above) shows the 'Fuzz Guitar' patch from the manual supplied with the Roland SH101\. This shares many attributes with the patch for the ARP Axxe. For example, the pulse wave again contributes most of the sound, although this time with an initial pulse width of 80 percent. However, Roland have made the pulse width follow the envelope shape, and have added some sawtooth wave, reducing the depth of the holes in the harmonic spectrum produced by the pulse wave alone. These are nice embellishments, and they add a pleasing movement to the sound that the Axxe patch lacks. But does this patch sound like a real guitar? No, of course it doesn't.

**Patch 3 -- The Minimoog**

While the Axxe and the SH101 are capable of producing both sawtooth and pulse waves simultaneously, the two waveforms are merely different outputs from the same oscillator. This means that they are always in perfect phase with one another, and that the summed waveform (notwithstanding changes of pitch, or the application of effects such as vibrato) is static. So let's now look at a synthesizer that uses independent oscillators to produce these waveforms.

Figure 7 (below) is the Electric Guitar patch from Tom Rhea's _Minimoog Sound Charts_ book. This mixes a pulse wave (Oscillator 2 contributing 70 percent in the mixer) with a ramp wave (Oscillator 1 contributing 50 percent in the mixer). Furthermore, this patch conforms more closely to my idea of an electric guitar, because the Sustain levels in both contour generators are zero. In addition, the decay of the filter cutoff frequency is somewhat faster than the decay of the amplifier. This attenuates the higher harmonics more quickly than the lower ones, and produces a more natural-sounding tail to each note. So, given that this is the revered Minimoog, the godfather, the source of all things wondrous and synthy... this must be the one that sounds like a real electric guitar. Right?

Wrong. While very pleasing to the ear (as are all three of these patches), the patch sounds not even remotely like an electric guitar. You could be lying near-catatonic on the floor after a particularly spectacular party, body suffused with harmful substances, your brain and ears filing divorce proceedings against the rest of your body... and _still_ you wouldn't be fooled. Clearly, the world does not permit practical analogue, subtractive synthesis to reproduce a guitar sound. Even the sound of the electric guitar has eluded us, except in the limited and meaningless case of playing the synth through an overdriven amplifier turned up to 11 on the Richter Scale. So, to finish this three-part discussion on what has transpired to be the non-synthesis of guitar sounds, I'm going to offer you a few more clues as to why this should be the case.

**Why Don't Synths Sound Like Electric Guitars?**

Let's consider something that the electric guitar has, but which an acoustic guitar does not -- pickups.

Figure 8 (right) shows a typical guitar pickup. This comprises a magnetised core with a coil of wire wrapped around it, all placed underneath but close to the metal wire that we commonly refer to as an electric guitar 'string'. Some basic physics (which we need not discuss) tells us that an electrical conductor [![](http://media.soundonsound.com/sos/oct01/images/synth_8_12s.gif)][6]vibrating in a magnetic field excites an electrical current, and it is this signal that is amplified and passed to the speaker for us to hear.

At this point, let's consider two things that seem unrelated but which, when taken together, prove to be vitally important. The first is: the distance over which the pickup can detect the string's motion is very short, so it is only sensitive to the small part of the string that lies immediately above it. The second is: when the string is stationary along the length detected by the pickup, no signal is generated.

Now consider the case where the pickup lies, say, one third of the distance from the bridge to the nut, as shown in Figure 8\. If you consider the wave motion, you will realise that the first harmonic (the fundamental) and the second harmonic each exhibit some motion immediately above the pickup. However, the third harmonic has a node at this position (ie. it is permanently stationary) and, therefore, this frequency -- which is present in the acoustic signal -- will be missing from the amplified signal (if this isn't clear, refer back to Part 28 of this series, in _SOS_ August 2001, or at [_www.soundonsound.com/sos/aug01/articles/synthsecrets28.asp_][7], which explains the importance of nodes in this context). Likewise, the sixth, ninth and other harmonics in this series will be missing.

Now consider Figure 9 (above), which shows what happens when you play a note one third of the way along the _neck_. In this case, it's the _second_ harmonic that is stationary above the pickup, along with the fourth, sixth, eighth... and so on. In other words, the pickup position acts as a comb filter whose harmonic spacing is dependent upon the pitch of the note you are playing.

Clearly, the relative amplitudes of the harmonics are greater when there is an anti-node (a position of maximum movement) immediately above the pickup, and less if a node lies above or close to the pickup. This means that the harmonic structure of the amplified signal is determined by the position of the pickup, as well as by the acoustic vibration of the string.

As an example of this, Figure 10 (below) shows the artificially simple case in which a sawtooth wave is 'played' through a pickup. As expected, the result is much like that of passing the wave through a comb filter.

Now let's view the effect of the pickup on the spectrum of an electric guitar (see Figure 11 below). The resulting harmonic structure is singularly unlike anything produced by our affordable subtractive synthesizers, so it's not surprising that our Axxe, SH101 and Minimoog patches lack realism.

By the way, you may have noticed that the low-frequency region of the spectrum in Figure 11 is much flatter than that of the common analogue waveforms (most of these conform to the 1/n amplitude relationship we've discussed before). This is because, on the electric guitar, the output of any harmonic is prop[![](http://media.soundonsound.com/sos/oct01/images/synth_12s.gif)][8]ortional to the velocity of its motion at the point on the string that lies immediately above the pickup. If you can picture the position of a bridge pickup and consider the displacements and velocities of the first few harmonics, you'll realise that the amplitudes produced by each are similar (don't worry if you can't envisage this... trust me). This means that until you approach the first harmonic with a node positioned above the pickup, the spectrum can be surprisingly flat.

Finally, I want to return to something that I touched very briefly upon in Part 28, where I stated that "the strings are not perfect harmonic oscillators. This is because they do not form perfect angles at the nut or the bridge. The finite cross-section of the string ensures that it curves at these points, thus making its active length slightly shorter than the idealised view would suggest. The degree to which this happens depends upon the wavelength and amplitude of the vibration, so the string appears shorter at high frequencies and high amplitudes than it does at low frequencies and low amplitudes. This sharpens higher, louder harmonics, further complicating any analysis of the string's harmonic spectrum, as well as the guitar body's response to it."

Figure 12 shows (in grossly exaggerated form) how this would be true for a string clamped at both ends. However, just to complicate matters still further, you should be able to see that it is only true on a guitar when the string bends 'down' with respect to the bridge and/or the nut. When it bends 'up' it lifts slightly at the edge of the nut and bridge, thus extending its effective length, and flattening the pitch for half the cycle. As for sideways and other angles... don't even ask. You don't want to know.

Anyway, consider the start of a note of any given pitch. You have just plucked the string, so its effective length is somewhat shortened by the initial high amplitude, and the overtones are _enharmonic_, meaning that they do not conform to the pure 1, 2, 3, 4... relationship of synthesizer oscillators. As the loudness of the sound decays, the effective length of the string becomes longer, and the pitch decreases.

As the amplitude decays further, the overtones become more nearly harmonic. However, while this is happening, the positions of the nodes and anti-nodes are sliding down the string, changing their positions with respect to the pickups, and thus modifying the harmonic mix of the electrical audio signal as they do so (by the way, it is this effect that the SH101 imitates by modulating the pulse width using the envelope generator. I wonder whether Roland's patch designers knew).

**Conclusions**

As you can see, the electric guitar is every bit as complex and unfathomable as the acoustic guitar. Indeed, it is even _more_ complex and unfathomable because, although the body resonances and their interactions with the strings are less significant, there are whole new families of effects to consider. All this... and we haven't touched upon multiple pickups, in-phase and out-of-phase pickup configurations, the phase shifts introduced by tone controls, and the capacitances of the cables (which can be very significant for such small signals).

At this point, I would like to draw Figure 13 for you to show some of this, adding the amplitude- and pitch- dependent comb filters and other effects. However, it wouldn't fit on an A4 page. So I think it's time to admit defeat and accept that, as I stated two months ago, we're never going to effectively imitate guitars using analogue synthesizers. [![](http://media.soundonsound.com/images/regulars/sos_end.gif)][9]

[0]: http://www.soundonsound.com/sos/Oct01/articles/synthsecrets30.asp
[1]: /search?url=%2Fsearch&Keyword=%22synth+secrets%22&Words=All&Summary=Yes
[2]: http://media.soundonsound.com/sos/oct01/images/synth1.gif
[3]: http://media.soundonsound.com/sos/oct01/images/synth_2_5.gif
[4]: http://media.soundonsound.com/sos/oct01/images/synth_6.gif
[5]: http://media.soundonsound.com/sos/oct01/images/synth_7.gif
[6]: http://media.soundonsound.com/sos/oct01/images/synth_8_12.gif
[7]: http://www.soundonsound.com/sos/aug01/articles/synthsecrets28.asp
[8]: http://media.soundonsound.com/sos/oct01/images/synth_12.gif
[9]: http://www.soundonsound.com