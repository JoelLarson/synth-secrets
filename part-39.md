# SYNTH SECRETS  
_Original article: [http://www.soundonsound.com/sos/Jul02/articles/synthsecrets0702.asp][0]_

![](http://media.soundonsound.com/sos/jul02/images/synth0702header.gif)

Original Photo courtesy of Zildjian

**Synthesizing realistic cymbals is complex, but not impossible -- after all, over 20 years ago, Roland's TR808 drum machine featured synthesized cymbals. We look at how they managed it, and attempt to create cymbals on another affordable analogue synth. This is the 39th article in a 63-part series. Read [all parts][1].**

**

---

****_Gordon Reid  
_**

Three months ago, in the May issue of _SOS_, I analysed and dissected the snare sounds produced by the Roland TR808 and 909 -- which, by common consent, are two of the 'classic' electronic drum sounds (see [www.soundonsound.com/sos/apr02/][2] articles/synthsecrets0402.asp). So, following the analysis of the cymbal in last month's _Sound On Sound_, I thought that it made sense to do the same this month for the cymbal sounds produced by both of these vintage drum machines. Of course, the cymbal sounds don't have quite the same hip _je ne sais quoi_ as the snares -- but surely if Roland were able to synthesize cy
[![](http://media.soundonsound.com/sos/jul02/images/fig01s.gif)][3]

Figure 1: A simple, subtractive model for the cymbal sound.

mbals in the early '80s, then despite all the complexity I detailed last month, it can't be that hard... can it?

**The TR909 Cymbal**

Figure 1, above, shows the cymbal patch I developed last month on my Nord Micro Modular, and Figure 2 (right) shows a simplified schematic for the TR909 cymbal sound generator. As you can see, they are utterly dissimilar. The key to this difference lies in the bottom left-hand block of Figure 2, the one that says 'six-bit data table'. Forget analogue FM synthesis, dynamic band-pass filters, and all the other paraphernalia I employed to try to recreate the cymbal's complex spectrum -- the TR909 dispenses with all of this by incorporating a digital sample of a genuine cymbal. In other words, at least one (and, in truth several more) of the instruments in the TR909 are generated by a 'samploid' drum machine. This means that parts of the TR909 are little different in concept and implementation from any other synth with PCM samples as oscillators.

The reason for Roland's decision is simple and compelling. It is _very_ difficult to emulate a cymbal using analogue synthesis. You might well have guessed this already if you were following the [![](http://media.soundonsound.com/sos/jul02/images/fig02s.gif)][4]

Figure 2: The TR909 cymbal sound generator.

ins and outs of last month's article, but if you need convincing further, I will demonstrate the point more clearly later. Before that, though, let's see what's going on in Figure 2\. Although we've largely avoided digital electronics in Synth Secrets, we should be able to understand the principles without too much trouble.

We'll start with the 30kHz oscillator to the upper left of the diagram. This is a clock that, when triggered, causes an address counter to revert to 'zero' and then step through the memory addresses of the sample data held in the ROM.

There are two outputs from the address counter. The first provides the information required by the TR909 to replay the audio data from memory. These exist in digital form, so the samples pass through a primitive digital-to-analogue converter (DAC) and the analogue signal produced by this then passes to a VCA for amplitude shaping. This is the audio path that runs horizontally along the bottom of Figure 2\.

The second output from the address counter contains the address data itself. To under
[![](http://media.soundonsound.com/sos/jul02/images/fig03s.gif)][5]

Figure 3: Turning an address into a contour.

stand this, imagine that the first five samples in the data table contain numbers that we will call 'v', 'w', 'x', 'y' and 'z' (the actual values are not important). The numbers are held in specific locations in the table that we will call '1', '2', '3', '4' and '5', because v, w, x, y and z are the first five samples.

Now look back at Figure 2\. As the audio values (v, w, x, y and z) are sent to their DAC, the numbers of the addresses that contain them -- in this case, 1, 2, 3, 4 and 5 -- are directed to a second DAC at the top of the diagram. The voltage produced by this DAC then passes through a device called an anti-log converter which takes the increasing voltage produced by the DAC, and turns it into a suitable envelope that controls the gain of the VCA in the signal path (see Figure 3, above).

At this point, you should ask why the TR909 employs such a complex mechanism to replay its cymbal sample. After all, doesn't the digitised audio contain all the information needed, thus rendering the VCA redundant? Unfortunately (for reasons we will not discuss here), this is not the case and, if replayed d
[![](http://media.soundonsound.com/sos/jul02/images/fig04s.gif)][6]

Figure 4: The TR808 cymbal block diagram.

irectly from the ROM, the samples do _not_ decay like a real cymbal. This means that something must shape the sound.

Now, if we need to shape the amplitude of the sound, it would seem straightforward to add a basic analogue contour generator and trigger this at the same time as the address counter. However, this would only work correctly if the pitch of the cymbal never changed. As you can see in Figure 2, you can tune the TR909's cymbal by altering the speed of the 30kHz oscillator that drives the counter, and this complicates matters considerably.

Think about it... If you increase the pitch of a digitised sound by increasing the clock rate, the data will be output more quickly, and you will reach the end of the samples more quickly than before. But if a conventional AR contour generator proceeds at the same rate, no matter what the speed of the digital clock, it's quite possible that the end of the samples will occur before the VCA is fully closed. If this happens, the sound will be truncated in the precise way that the sound of a real cymbal is not. So Roland made the decay rate of the AR envelope dependent upon the progress of the address counter, thus ensuring that, no matter how much you mess with the clock, the VCA always shapes the sound correctly. Clever, isn't it?

Having created the basic sound and shaped its amplitude using a VCA, you should now be able to send it to the outside world without further fuss. No? Umm... no. The missing element is the low-pas
[![](http://media.soundonsound.com/sos/jul02/images/fig05s.gif)][7]

Figure 5: The TR808 cymbal in Synth Secrets format.

s filter that lies between the VCA and the output. This is required because the signal suffers from quantisation noise and aliasing. Fortunately, the unwanted components generated by these problems lie predominantly at high frequencies, so a suitably chosen low-pass filter eliminates the worst of them without introducing unacceptable signal degradation.

And there you have it... the TR909 cymbal passes through an analogue VCA and an analogue low-pass filter. But it isn't an analogue sound. It's a set of digital samples replayed through a bit of analogue electronics.

**The TR808 Cymbal**

To find a truly analogue attempt at synthesizing cymbals, we need to step back a bit further in time, and look at that other doyen of analogue drum machines, the Roland TR808\.

Figure 4 (below left) shows the block diagram for the TR808 cymbal. I have reproduced this from Roland's documentation, removing all sorts of extraneous stuff to clarify things as much as possible. Figure 5 (shown on the next page) shows the same thing in a format more familiar to long-standing readers [![](http://media.soundonsound.com/sos/jul02/images/fig06s.gif)][8]

Figure 6: Recreating the TR808 cymbal on a modular synthesizer.

of this series. As you can see, there's nothing digital going on here.

The initial sound generator comprises six square-wave oscillators tuned enharmonically, and mixed to create a complex spectrum. If you remove all the low harmonics from the mix, this produces a moderately dense cluster of partials in the mid and high frequencies.

The mixed signal from the six oscillators is split into two bands by a pair of band-pass filters. The lower frequency band then passes through a VCA controlled by an AR contour generator. The TR808's Decay control affects the decay rate of this envelope, thus allowing you to extend or curtail the duration of the low-frequency components in the final sound.

The upper band is further split into two signal paths that pass through independent VCAs controlled by their own contour generators. The upper of the two, um, upper bands has the shortest Decay. The lower of the upper bands has a Decay that lies somewhere near the centre of the range of the low band's variable AR control. This inequality of decay times allows the TR808 to change the mix of lower-, mid- and higher-frequency components as the sound progresses.

All three bands then pass through high-pass filters to remove more yet low-frequency components, before a user-controlled mixer recombines them into a single signal (the TR808 tone control affects this mix of low, mid and high bands). Finally, an amplifier determines the loudness of
![](http://media.soundonsound.com/sos/jul02/images/fig07.gif)

Figure 7: The MS20 oscillators producing an enharmonic timbre.

the output.

**Recreating The TR808**

The circuit which creates the TR808's cymbal is very elegant, and it's not trivial to recreate it on a conventional analogue synthesizer. Just for fun, I've drawn Figure 6 (below), which shows a modern analogue synth -- an Analogue Systems RS Integrator -- configured to emulate the TR808 cymbal. That's right... this monster of a patch is _just_ the cymbal in Figure 5\. Note that I have not set the knobs on these modules to appropriate values... simply selected and patched the modules needed to do the job.

Adding up the cost of the modules, cases and PSUs in Figure 6, I reckon that we're looking at a collection of synth modules worth around £1500\. Of course, unlike the TR808 cymbal circuit, this Integrator could produce a zillion and one other sounds, and with far higher fidelity than any analogue drum machine. Nonetheless, the diagram shows us that Roland's engineers were very smart cookies indeed.

Comparing Figures 1 and 5, we can see that they share many concepts. OK, the Roland uses multiple oscillators whereas the patch I designed used FM to generate a complex spectrum, but both models split the signal into high and low frequency bands and shape them to imitate the response of a real cymbal. If there is one area in which the TR808 falls short, it is in its lack of dynamic filtering. Last month's analysis showed that this was an important element in the sound, but in the early '80s it would probably have been too complex and too expensive to incorporate it into the TR808\.

**Synthesizing The Cymbal Sound: Part 1**

Rather than patch the unrealistic monster in Figure 6, I'm now going to try -- and, as you will see, fail -- to create an acceptable cymbal sound on one of the common analogue monosynths that we've been using in recent parts of this series. The ARP Axxe and Roland SH101 are no good for this, because they are single-oscillator instruments with a single filter and single signal path. The Minimoog is also a non-starter. Only the Korg MS20 (shown above) approaches the complexity required. With its two signal paths and four filters, we might just about be able to patch a passable sound on it.

Let's start with the oscillators and, in particular, the primitive ring modulator on VCO2\.
![](http://media.soundonsound.com/sos/jul02/images/fig08.gif)

Figure 8: Producing narrow bands of highly emphasised frequencies.

This uses a switching circuit to modulate the pulse wave output from VCO1 (whatever the knob's setting) with the pulse wave generated by DCO2\. This doesn't produce the complex cluster of partials generated by FM, and it's nowhere near as flexible as I would like, but it's the best that the MS20 can offer, so I shall attempt to use it to create the signal components needed. Sadly, a ring modulator is not best suited to this task and, although it produces four partials for each pair of VCO1 and VCO2 harmonics, the resulting output is still not sufficiently complex to resemble the metallic 'ting' we require.

I shall attempt to insert more enharmonic elements into the sound by adding the unmodulated output from VCO1, adjusted to be as 'out of tune' as possible when compared to VCO2 (see Figure 7, above). But there's a problem here... the tuning of VCO1 affects the timbre produced by VCO2's ring modulator, so I shall have to find settings that satisfy both requirements. The truth is, I'm going to fail to create anything as good as the TR808, but we'll press on, and see if we can use the rest of the MS20 to improve matters.

I'll remove the low-frequency components generated by the oscillators by opening the low-pass filter and then setting the high-pass filter so that only a narrow band of frequencies survives filtering. In addition, I will emphasise the resulting band by setting the 'Peak' (Korg's term for filter resonance) to a high value for both filters, so that they are on the edge of self-oscillation (see Figures 8 and 9, left).

The sound I've produced still bears no resemblance to that of a cymbal, and the major reason for this lies in the paucity of signal components. Unfortunately, the MS20 is incapable of generating any more partials, so we must now apply a little lateral thinking if we are going to add more 'body' to the sound.

There is one way to do this, although I had hoped to avoid it because, as far as synthesis goes, it lands us back in the 1960s. But there seems to be no choice; the only place to obtain more body is from the MS20's noise generator. So now we must turn our attention to the yellow (audio signal) cables that I have inserted into the MS20's patch bay (see Figure 10, above).

As you can see, I've taken the 'white' output from the noise
[![](http://media.soundonsound.com/sos/jul02/images/fig09s.gif)][9]

Figure 9: The response of the filter settings in Figure 8\.

generator and directed this to the signal input of the External Signal Processor (or ESP), turning the input amplifier gain to maximum so that it distorts, thus roughening the sound a little. I have then adjusted the band-pass filter in the ESP to ensure that only a narrow band of high-frequency noise emerges, and directed this to the patchable VCA, and then on to the signal input that lies before the filters in the main signal path.

If you don't insert a patch cable into the patchable VCA's Gain control input, it is controlled by Envelope Generator 1, which produces a simple ASR contour. So, to shape the amplitude of this part of the sound, I must tap the keys when playing, not hold them down for an extended time. This is an acceptable compromise, and the settings (Attack to '0', and Release to '8'), as shown in Figure 11 (below), ensure that the noise signal is passed with instant Attack, and that its amplitude decays as the sound progresses.

While I have you looking at the patchbay, you should notice that there is a red (control signal) patch lead running from the Inverted output of EG1 to the 'Total' modulation input. To understand what this is doing, you must look at the modulation controls in Figure 11\. You can see here that the 'MG/T.Ext' parameter for the high-pass filter is set to '7'. This means that the inverted Attack/Sustain/ Release contour is affecting the cutoff frequency of the high-pass filter, increasing the
[![](http://media.soundonsound.com/sos/jul02/images/fig10s.gif)][10]

Figure 10: Using the patchbay.

lowest pitch of the spectral content of the sound as it progresses.

Finally, I will shape the amplitude of the composite sound using Envelope Generator 2, giving the sound an instant Attack, and consistent Decay and Release of '2', thus ensuring that the envelope is the same whether I release the key or not. These settings also explain why the Sustain stage of EG1 is not a problem... Even if I hold a key for too long, the VCA controlled by EG2 will curtail the sound. What EG1 is doing, therefore, is changing the relative mix of the noise and the spectral components in the signal. It's a crude attempt to imitate one of the features of the multiple signal paths in Figure 5, but it's the best that the MS20 can offer.

If you recreate the sound in Figure 11, you will find that it is incredibly sensitive to tiny changes in the settings of the oscillators and main filters. You'll also find that, at best, it has some of the characteristics of a cymbal without ever sounding anything like a cymbal. This is disappointing, but to be expected. After all, as far as I remember, none of the patch charts supplied with analogue synths contained a cymbal patch, so you can be fairly sure that no affordable synth of this type was
[![](http://media.soundonsound.com/sos/jul02/images/fig11s.gif)][11]

Figure 11: The MS20 cymbal patch.

ever particularly well-suited to reproducing this kind of sound.

**What Went Wrong?**

Figure 12 (above) shows the signal path for the patch in Figure 11, and when we compare this with the model in Figure 1, we can see why the MS20 cannot do the job we have asked of it. As already noted, the initial sound lacks a metallic 'ring', and much of the body of the sound comprises noise rather than discrete signal components. In addition, the 'impact' synthesis is missing, and the contour in the body affects only the VCA, not the band-pass filter. Ultimately, these and other limitations have proved to be too great, and so the MS20 proves inadequate for the task.

You might ask, therefore, whether this invalidates the patch in Figure 11\. I don't think that it does. It is an extremely aggressive
[![](http://media.soundonsound.com/sos/jul02/images/fig12s.gif)][12]

Figure 12: What's happening in the patch in Figure 11\.

sound that would punctuate any rhythm track. Just don't believe that it sounds like a real cymbal, because it doesn't.

**Synthesizing The Cymbal Sound: Part 2**

Let's now returns to the Nord Modular patch that I developed last month. This made a much better job of creating the semblance of a cymbal than does the MS20, but still leaves room for a single, enormous improvement...

I suspect that Roland adopted its approach of using multiple oscillators because it's cheap and easy to build coarse square-wave oscillators. However, a rival company, Korg, discovered that using multiple pairs of _modulated_ square-wave oscillators creates a much more authentic metallic timbre. So, while Roland seemed happy with the TR808, Korg was manufacturing drum machines such as the Rhythm 55, which offered cymbal sounds that were an order of magnitude more complex -- and more realistic -- than those produced by the Roland. And therein lies the secret to affordably synthesizing all manner of metallic percussion.

Given the nature of the Nord Modular, it's simple to enhance last
[![](http://media.soundonsound.com/sos/jul02/images/fig13s.gif)][13]

Figure 13: Frequency-modulating multiple pairs of oscillators in the Nord Modular.

month's patch by adding more pairs of modulated oscillators, detuning them in ways that sound appropriate, and then mixing them to a single signal (see Figure 13 on the next page).

The results are stunning, capturing the very essence of metalwork. Playing with the oscillator waveforms and frequencies, together with the contours controlling the filter and amplifier in the rest of the patch (shown in Figure 14 on the next page) produces large cymbals, small cymbals, Eastern cymbals, rides, crashes, hi-hats, the finger cymbals in tambourines... The possibilities (which we will explore in more detail next month) are enormous.

**Epilogue**

Let's finish by re-evaluating what we have learned about cymbals. Last month, and the month prior to that, I discussed the nature of the cymbal and conducted an empirical analysis, using this to create a recognisable cymbal sound with just a couple of digital oscillators, filters and amplifiers within a Nord Micro Modular. This month I showed that affordable analogue synths are unsuitable for synthesizing cymbals, but that -- if we learn the lessons of the clever, dedicated sound generators in drum machines -- we can create much better emulations using powerful modular synths or software synths.

Of course, you might assume that in these days of supercomputers, Pentium-driven software synths, and workstations containing up to a dozen DSPs, it will soon be possible to step beyond Figure 14, a
[![](http://media.soundonsound.com/sos/jul02/images/fig14s.gif)][14]

Figure 14: Using multiple frequency-modulated oscillators to create a better cymbal sound. 

nd model the precise sound of a cymbal without resorting to modulated oscillators or samploid synthesis. However, this belief is probably flawed, for the following reasons.

Last month, I stated that an analysis of the cymbal is far beyond the scope of these articles. What I omitted to say is that a complete analysis of the cymbal currently remains beyond the scope of _anybody_! Cast your mind back to the analogy I made two months ago, where I related the means by which a cymbal produces its sound to what happens when a stone is thrown into a pond. Now try to imagine what would happen if the ripples produced by the impact took days to dissipate, interacting and interfering with one another everywhere on the water's surface, and doing so differently at every point and at every moment in time. Now add complicating factors such as, for example, an uneven pond-bed, and make the water more viscous at some points than it is at others... A full analysis of this is all but impossible, and a numerical model of its behaviour would require almost infinite processing bandwidth. Thankfully, both the Korg Rhythm 55 and the Nord patch in Figure 14 prove that (unlike our attempts at guitar synthesis earlier in this series) we need neither a PhD in acoustics nor God's own Personal Computer to synthesize acceptable cymbal sounds. And that news, surely, will come as a relief to synthesists everywhere. [![](http://media.soundonsound.com/images/regulars/sos_end.gif)][15]

[0]: http://www.soundonsound.com/sos/Jul02/articles/synthsecrets0702.asp
[1]: /search?url=%2Fsearch&Keyword=%22synth+secrets%22&Words=All&Summary=Yes
[2]: http://www.soundonsound.com/sos/apr02/
[3]: http://media.soundonsound.com/sos/jul02/images/fig01.gif
[4]: http://media.soundonsound.com/sos/jul02/images/fig02.gif
[5]: http://media.soundonsound.com/sos/jul02/images/fig03.gif
[6]: http://media.soundonsound.com/sos/jul02/images/fig04.gif
[7]: http://media.soundonsound.com/sos/jul02/images/fig05.gif
[8]: http://media.soundonsound.com/sos/jul02/images/fig06.gif
[9]: http://media.soundonsound.com/sos/jul02/images/fig09.gif
[10]: http://media.soundonsound.com/sos/jul02/images/fig10.gif
[11]: http://media.soundonsound.com/sos/jul02/images/fig11.gif
[12]: http://media.soundonsound.com/sos/jul02/images/fig12.gif
[13]: http://media.soundonsound.com/sos/jul02/images/fig13.gif
[14]: http://media.soundonsound.com/sos/jul02/images/fig14.gif
[15]: http://www.soundonsound.com