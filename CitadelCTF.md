# Citadel CTF
## Zahard's Welcome
The base of Citadel rises before you, its great doors sealed with fractured steel and dead circuitry.  
Faded corporate protocols still hum in the lock, relics of the world that fell.   

Those who came before tried to climb but all failed. Their echoes linger as fragments of voices,  
reminders of broken attempts to free humanity. Now you have chosen to take their place. You will be the  
one to scale the Citadel and finish what they could not.   

The voices of the fallen whisper through the static: "The path begins in the gathering place. There,  
candidates are chosen". Here is your invitation.  

Step into the gathering place where all climbers are briefed before the ascent.  
### Solve
**Flag:** `citadel{7h3_c174d3l_b3ck0n5}`
I joined the discord server and simply looked through all the channels until I found the flag in the rules channel's description.  
## The social network
 
🗼OSINT pt1: The ascent begins. The first floor is not metal or binaries but of memory. Among the echoes, one voice lingers, of an early climber. He was among the earliest to challenge the Citadel, and though he failed, his traces remain scattered across the ruins of the old world.

It is said that the key to the next floor can be found by tracing the socials of this legendary climber. Start by checking out citadweller on Instagram.

### Solve
First, we searched for citadweller on Instagram — the highlights gave away the first half of the flag. Then we hopped over to X, found the same username, and there it was — the second half   waiting for us.  

Flag: ```bash citadel{17_1s_jus7_7h3_b3g1nn1ng}```
## track 8
Bypassing the second chamber leads to an empty floor except for a single artifact in the center: an old  
MP3 player, scratched and worn. On its surface, a cipher is etched, a message left behind for anyone  
who can decode it  
  
twj eys zpr ukm 'viamnwqw' bx lzgo: esmqqui{yyr_oshwwcm_bwupa}   

When you power it on, the sound fills the chamber. The tracks play like whispers from a lost world, and  
you recognize it as a song from Panchiko’s latest studio album, particularly track no. 8. Its title  
feels familiar, hinting at a famous cipher. Decrypt it by using the album name as your key and continue  
your ascent.  
### Solve
**Flag:** `citadel{add_vinegar_twice}`
I searched up panchiko's latest studio album and used that as the key for the vigenere cipher to get   
` now use the key 'panchiko' on flag: rigckmv{osd_ikumqog_tjkjm}`  
## Omniscient Flag's metadata
As you step into the second chamber, a figure manifests. Before you stands a forgotten deity, a dead  
god spoken of only in whispers. Known by countless names: “Apostle of Epilogue and Eternity”, “Lone  
Messiah” and many more lost to time.   

They leave nothing but a single image, a relic carrying his final secret. Hidden within its layers lies  
the key to ascend to the next chamber.  
### Solve
**Flag:** `citadel{add_vinegar_twice}`
DSomething about the picture seemed off, so I decided to dig deeper. With the help of an LLM, I realized there was  
actually a PNG image embedded within the JPG. I then used Steganographer Separator to extract it,  
revealing another image — and this one had the flag written right across it.oing the above , we get   
`citadel{add_vinegar_twice}`
## Test of Sweetness 


This floor feels like a digital world. The space is an illusion, all pink and sweet, stretching around  
you in impossible patterns. Here, you are no longer a climber but just another user.   

Ahead, a door glows faintly. It is the only path forward and requires a level of authority you do not  
yet have. Fragments of session memory flicker, hinting at what it might take to gain higher access.   

Challenge: https://testofsweetness.citadel.cryptonitemit.in  
### Solve
**Flag:** `citadel{fru1tc4k3_4nd_c00k13s}`
I read this and thought immediately of cookies.I turned out to be right but the name and the value proved  
to be a setback and after a lot of trying, I figured out the difference between the name and the value and put   
the value as admin to get higher access and hence the flag.  
## Rotten Apple 
Among the debris of this floor, you find a relic of sound: An album which turns out to be  
D>E>A>T>H>M>E>T>A>L by Panchiko, a long lost album. But the music is warped, as though it has undergone  
disc rot.  


The path forward is hidden in the distortion. Similar to how the album was warped, the password to the  
next floor has been warped first by a factor of 47, then by a factor of 13. Untangle these changes to  
reveal the code and continue your ascent.  
  
4:R256=Y3oRRoP0#~%Ro?A  
### Solve
**Flag:** `citadel{b3tt3r_ROTt3n}`
I used ROT-13 first and then ROT-47 to get the flag.


## Randomly Accessed Memories

On your ascent to this floor, you hear these fragments being played back —

```bash
clone it, pull it, reset it, stage it, 
commit, push it, fork, rebase it. 
merge it, branch it, tag it, log it, 
add it, stash it, diff, untrack it … 
```

You look around and discover a chamber containing a vast archive of Daft Punk’s music, intertwined with cryptic commits left behind by other musicians. They seem ordinary at first glance, but not everything in the history is what it seems. The archive:
 https://github.com/evilcryptonite/daft-punk-archive

### Solve 
We explored the commit history looking for clues and, in the process, discovered the third chunk first,  
followed by the second and first chunks in that order. After arranging them correctly according to their  
numbering, we decoded the combined string using the From Base64 operation in CyberChef.  

Flag: ```bash citadel{w3_4r3_up_4ll_n1t3_t0_g1t_lucky} ```  

## Selected Ambient Work  
The symphonic adventure does not end here. On the next floor, a single song keeps echoing through the  
floor, repeating in a haunting loop. Amid the sound, you find a note left by a past candidate. It hints  
that the song holds a secret message, hidden in plain sight, much like how Aphex Twin concealed his  
face within his music with the help of spectrograms.  

To move forward, you must find the message hidden in this sound.  

Note: Separate the words in the flag with _ and make it UPPERCASE. Example:   
citadel{S3L3CT3D_AMB13NT_W0RK}  
### Solve
**Flag:** `citadel{1_LOV3_1DM`
I was stuck on this for a while as I figured out it was morse but it also had beats  
along it. Upon re-examining the spectrogram after numerous times, we saw the text of citadel { with morse in between  
which gave us the hint. I noted the morse in between the brackets to solve it.  
## The Robot's Trail  
You enter a virtual maze, a labyrinth of shifting corridors and endless paths. A guardian robot patrols  
the floor, leaving a trail behind as it moves. Follow the path it carves, trace its movements  
carefully, and uncover the key it leads you to. Only by following the robot’s trail can you reach the  
door to the next floor.   

Challenge: https://therobotstrail.citadel.cryptonitemit.in  
### Solve 
**Flag:** `citadel{p4th_tr4v3rs4l_m4st3ry_4ch13v3d}`
Seeing the challenge, I immediately knew it was a traversal challenge.  
By first inspecting the page(`<div class="hidden">
        <p>Start by checking what this site tells search engine bots in <a href="/robots.txt" style="color: #00bcd4;">robots.txt</a></p>`) and then just following the clues, I got the flag.
## Rotting In The Deep
The floor is quiet, almost unnervingly so – like the Citadel has paused to take your measure. A soft  
ring of presence settles around the chamber, the kind that marks a true landing: from here, it will ask  
for more and, in return, grant more. Etched into its surface is a sequence of numbers, worn and faint,  
as if time itself is eating them away. A whisper from the echoes guides you:  

The message lies beneath the surface. Push it three steps forward in the cycle of life, and only then  
will the words emerge from the void.  
### Solve
**Flag:** `citadel{br0_r34lly_unr0tt3d_m3_b4ck_t0_l1f3}`
By seeing the python script, I understood we have to use +3 and use something to get 6895840967002953721051398351211751734500850509315790892845302801984496338433523326225010635779036738800318 as the  
output. Thus by applying a shift of -3 and then converting the long into bytes, we got the flag.  


