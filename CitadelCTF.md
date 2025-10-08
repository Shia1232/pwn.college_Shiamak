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

### Coco Conjecture
The door to the next floor is guarded by a figure who calls herself "The Dragon CEO". She does not  
speak of mercy or choice, only of order and efficiency.   

 To enter the next chamber, you must complete the task presented by her. Complete it exactly as  
 instructed, achieving operational efficiency by her standards, and the path forward will open.  

 
Connection: nc chall_citadel.cryptonitemit.in 61234 
### Solve
**Flag:** `citadel{k1ryu_c0c0_h4s_4_g0_4t_4n_uns0lv3d_m4th3m4t1cs_pr0bl3m}`
```
import socket
import re

# Memoization cache for previously seen numbers
cache = {1: 0}

def collatz_steps(n):
    original = n
    steps = 0
    while n != 1:
        if n in cache:
            steps += cache[n]
            break
        if n % 2 == 0:
            while n % 2 == 0:
                n >>= 1  # fast division by 2
                steps += 1
        else:
            n = 3 * n + 1
            steps += 1
    cache[original] = steps
    return steps

HOST = "chall_citadel.cryptonitemit.in"
PORT = 61234

with socket.create_connection((HOST, PORT)) as s:
    f = s.makefile('rwb')
    while True:
        line = f.readline()
        if not line:
            break
        line_str = line.decode().strip()
        print(line_str)  # Optional: see server messages

        # Check for the flag
        flag = re.search(r'citadel\{.*?\}', line_str)
        if flag:
            print("\n🎯 FLAG:", flag.group(0))
            break

        # Extract round number
        m = re.search(r'Round \d+: (\d+)', line_str)
        if m:
            n = int(m.group(1))
            ans = collatz_steps(n)
            # Send answer immediately
            f.write(f"{ans}\n".encode())
            f.flush()
```
We ran `k.py` in WSL using `python3 k.py`. The script connected to `chall_citadel.cryptonitemit.in:61234` and received numbers each round. We calculated how many Collatz steps each number took to reach 1, using bit shifting and   memoization to speed things up. After sending all the correct answers, the flag appeared in the terminal.  
## schlagenheim
Your quest continues, but you feel something odd about this room. The only artifact on this floor is a   
corrupted file held in the hands of a jet-black statue, frozen in the pose of a band mid-performance.  
The passcode to the next floor is hidden within this piece of music, but it can’t be played, as if the  
wrong extension has scrambled it.  

 You must take the corrupted file and repair it to reveal the true code that will unlock the door  
 forward.  
 ### Solve
 **Flag:** `citadel{8lackM1D1wa5c00l}`
 The original WAV file turned out to be corrupted and couldn’t be opened properly. However, the hint  
 mentioned something related to a “MIDI” file, which pointed toward a possible format mismatch. By  
 inspecting the file in a hex editor, it became clear that the data structure matched that of a MIDI file  
 rather than a WAV. After correcting the file extension and playing it through an online MIDI player, the audio output revealed the hidden flag clearly.  
 ## XOR Slide  
 You realise that a previous climber has set up a puzzle in what was otherwise an empty room, blocking  
 the entrance to the next floor on the ceiling. You must slide the blocks forming the pyramid to create  
 a path above.  
 ### Solve
 **Flag:** `citadel{8lackM1D1wa5c00l}`

I worked on recovering the plaintext from a ciphertext that was encrypted using a sliding XOR scheme. The approach was to  
XOR each ciphertext byte with its corresponding known wrapper byte and the previously recovered keystream byte,gradually  
reconstructing the keystream as I went along. I ran into a couple of small struggles at first—figuring out the correct wrapper  
alignment and dealing with an off-by-one error that kept producing gibberish—but once I fixed those, the rest fell into place and the  
flag finally appeared clearly.  
## The Sound of Music
OSINT pt2: citadweller had a newfound interest in tracking the music they last listened to and  
posting ratings of new albums on various online platforms.  
  
The flag is hidden in these digital footprints across music platforms and split into three segments.  
You will need to find all three to uncover the complete code and move on to the next floor.  
### Solve  
**Flag:** `citadel{c0mputers_st0pped_exchang1ng_1nf0rmat10n_n_started_shar1ng_st0r1es_n_then_they_were_n0where_t0_be_f0und}`

After following the hints, I found the first part of the flag on Last.fm under the user citadweller. The second segment appeared in RateYourMusic reviews,  
and a Spotify link revealed the final part. Once I combined all three pieces, the full flag became clear, letting me move on to the next floor.  
## Echoes and Pings  
You come across the remnants of a fallen corporation and the final network communication ever sent by  
them.   

Allegedly, the message contained an image that predicted the rise of the Citadel. Your task is to  
uncover what was sent and decode the communication to extract the passcode that will unlock the  
next floor.  
### Solve
**Flag** `citadel{1_r34lly_w4nt_t0_st4y_4t_y0ur_h0us3}`
I analyzed the pcap file's protocol hierachy, we see an image was sent.  
On analyzing the ICMP packets we see a jpg was sent on it. After spending a lot of time and admittedly a lot  
of chatgpt-ing we built a script to uncover the image.  
## The Ripper 
The guardian of this floor steps from the shadows. Known only as Jack the Ripper, he watches you  
carefully. He proclaims himself merciful and hands you a word list to help. He asks you to find the  
passcode hidden in the file. The word list is your only aid. Only by combining the two correctly, can  
you uncover the key and move on to the next floor.   


Flag format: citadel{password}  
### Solve  
**Flag:**  `citadel{fake_flag_4_fake_pl4y3rs}`
I put the hash into an online tool to uncover the possible hashing protocols it could follow.  
I tried bcrypt and got the flag using the password fake_flag_4_fake_pl4y3rs. 
## AetherCorp NetprobeX

You step into a simulation of the past, entering the ruins of AetherCorp, the most ambitious corporation in history, and their creation, NetProbeX, once the most advanced networking tool the world had ever seen. The floor reconstructs the events that led to humanity’s downfall.

Your task is to find the hidden backdoor in NetProbeX, the flaw that triggered the collapse. By uncovering it, you can reverse the damage and retrieve the passcode to advance to the next floor.

### Solve
**Flag:** `citadel{bl4ck51t3_4cc3ss_gr4nt3d}`  
In order to try to find the loopholes in the website login database, we found SQL injecting could be one of the ways. But none of the usual commands worked , upon browsing we found %0A could be used before each command instead of ' and it worked. So we tried out the UNION SELECT attack along with injecting NULL.Until the no of NULL s exceeded the no of columns which were getting selected by the original SQL query, a particular error was showing error but the page changed when there were 3 Null. We got a list of employees but it didn't provide any useful clue. So then we used ls command to view all the files, we found potential files that could hold the key and then found blacksite_key.dat file and got the flag by reading it.
## Feels Like We Only Go Backwards  
After finding the backdoor and making your way to the next floor, you step into a chamber awash with  
shifting colors and swirling echoes, a concert frozen in time. Kevin Parker stands at the center, his  
riffs bending reality around him. To ascend, you’ll need to join the session on his terms: push your  
voice further than comfort, align yourself with the number he hides in the haze, and piece together the   
melody concealed within layers of reverb. Only then will the music open the way upward.  
### Solve
**Flag:** `citadel{f0r_0n3_m0r3_h0ur_1_c4n_r4g3}`
Using,[Dogbolt](https://dogbolt.org/?id=2d45bdb9-e245-4ac3-bff3-71fe224d8bfa#Ghidra=438) I converted the file to code.   
The script helped me a lot.  
```
#include "out.h"



void _DT_INIT(void)

{
  __gmon_start__();
  return;
}



void FUN_00101020(void)

{
  (*(code *)(undefined *)0x0)();
  return;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int puts(char *__s)

{
  int iVar1;
  
  iVar1 = puts(__s);
  return iVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

size_t strlen(char *__s)

{
  size_t sVar1;
  
  sVar1 = strlen(__s);
  return sVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int printf(char *__format,...)

{
  int iVar1;
  
  iVar1 = printf(__format);
  return iVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

size_t strcspn(char *__s,char *__reject)

{
  size_t sVar1;
  
  sVar1 = strcspn(__s,__reject);
  return sVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

char * fgets(char *__s,int __n,FILE *__stream)

{
  char *pcVar1;
  
  pcVar1 = fgets(__s,__n,__stream);
  return pcVar1;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int setvbuf(FILE *__stream,char *__buf,int __modes,size_t __n)

{
  int iVar1;
  
  iVar1 = setvbuf(__stream,__buf,__modes,__n);
  return iVar1;
}



void __isoc99_scanf(void)

{
  __isoc99_scanf();
  return;
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

void exit(int __status)

{
                    // WARNING: Subroutine does not return
  exit(__status);
}



// WARNING: Unknown calling convention -- yet parameter storage is locked

int getc(FILE *__stream)

{
  int iVar1;
  
  iVar1 = getc(__stream);
  return iVar1;
}



void __cxa_finalize(void)

{
  __cxa_finalize();
  return;
}



undefined8 FUN_00101100(void)

{
  setvbuf(stdout,(char *)0x0,2,0);
  setvbuf(stdin,(char *)0x0,2,0);
  puts(&DAT_00104080);
  FUN_001014c0();
  return 0;
}



void processEntry entry(undefined8 param_1,undefined8 param_2)

{
  undefined1 auStack_8 [8];
  
  __libc_start_main(FUN_00101100,param_2,&stack0x00000008,0,0,param_1,auStack_8);
  do {
                    // WARNING: Do nothing block with infinite loop
  } while( true );
}



// WARNING: Removing unreachable block (ram,0x00101193)
// WARNING: Removing unreachable block (ram,0x0010119f)

void FUN_00101180(void)

{
  return;
}



// WARNING: Removing unreachable block (ram,0x001011d4)
// WARNING: Removing unreachable block (ram,0x001011e0)

void FUN_001011b0(void)

{
  return;
}



void _FINI_0(void)

{
  if (DAT_0010e4a8 != '\0') {
    return;
  }
  __cxa_finalize(PTR_LOOP_00104068);
  FUN_00101180();
  DAT_0010e4a8 = 1;
  return;
}



void _INIT_0(void)

{
  FUN_001011b0();
  return;
}



undefined8 FUN_00101240(char *param_1)

{
  size_t sVar1;
  long lVar2;
  byte local_88 [48];
  short local_58 [40];
  
  local_88[0] = 3;
  local_88[1] = 7;
  local_88[2] = 0xb;
  local_88[3] = 0xf;
  local_88[4] = 0xb;
  local_88[5] = 7;
  local_88[6] = 3;
  local_88[7] = 7;
  local_88[8] = 0xb;
  local_88[9] = 0xf;
  local_88[10] = 0xb;
  local_88[0xb] = 7;
  local_88[0xc] = 3;
  local_88[0xd] = 7;
  local_88[0xe] = 0xb;
  local_88[0xf] = 0xf;
  local_88[0x10] = 0xb;
  local_88[0x11] = 7;
  local_88[0x12] = 3;
  local_88[0x13] = 7;
  local_88[0x14] = 0xb;
  local_88[0x15] = 0xf;
  local_88[0x16] = 0xb;
  local_88[0x17] = 7;
  local_88[0x18] = 3;
  local_88[0x19] = 7;
  local_88[0x1a] = 0xb;
  local_88[0x1b] = 0xf;
  local_88[0x1c] = 0xb;
  local_88[0x1d] = 7;
  local_88[0x1e] = 3;
  local_88[0x1f] = 7;
  local_88[0x20] = 0xb;
  local_88[0x21] = 0xf;
  local_88[0x22] = 0xb;
  local_88[0x23] = 7;
  local_88[0x24] = 3;
  local_58[0] = 0xc9;
  local_58[1] = 0xde;
  local_58[2] = 0xfd;
  local_58[3] = 0xe0;
  local_58[4] = 0xe7;
  local_58[5] = 0xea;
  local_58[6] = 0xf9;
  local_58[7] = 0x120;
  local_58[0x20] = 399;
  local_58[0x21] = 0x11c;
  local_58[0x22] = 0x183;
  local_58[0x23] = 0x11c;
  local_58[8] = 0xff;
  local_58[9] = 0x9c;
  local_58[10] = 0x121;
  local_58[0xb] = 0xfc;
  local_58[0xc] = 0x9f;
  local_58[0xd] = 0x124;
  local_58[0xe] = 0xb7;
  local_58[0xf] = 0x118;
  local_58[0x24] = 0x1b1;
  local_58[0x10] = 0x135;
  local_58[0x11] = 0xbc;
  local_58[0x12] = 0x141;
  local_58[0x13] = 0xcc;
  local_58[0x14] = 0x12d;
  local_58[0x15] = 0x148;
  local_58[0x16] = 0xd9;
  local_58[0x17] = 0x164;
  local_58[0x18] = 0x15f;
  local_58[0x19] = 0x142;
  local_58[0x1a] = 0xef;
  local_58[0x1b] = 0x154;
  local_58[0x1c] = 0x15d;
  local_58[0x1d] = 0x100;
  local_58[0x1e] = 0x175;
  local_58[0x1f] = 0x160;
  sVar1 = strlen(param_1);
  if (sVar1 == 0x25) {
    lVar2 = 0;
    while (local_58[lVar2] ==
           (ushort)((ushort)local_88[lVar2] + ((ushort)lVar2 & 0xff) * 5 +
                   (ushort)(byte)param_1[lVar2] * 2)) {
      lVar2 = lVar2 + 1;
      if (lVar2 == 0x25) {
        return 1;
      }
    }
  }
  return 0;
}



void FUN_00101340(void)

{
  int iVar1;
  char *pcVar2;
  size_t sVar3;
  long local_90;
  char local_88 [128];
  
  puts("\n=== LEVEL 2 ===");
  puts("it\'s time for some mind mischief! ");
  puts("what number is kevin parker thinking of right now: ");
  iVar1 = __isoc99_scanf(&DAT_00102015,&local_90);
  if (iVar1 != 1) {
    puts("Bad input.");
                    // WARNING: Subroutine does not return
    exit(0);
  }
  if (4 < local_90 - 0x1e6d9e9c7U) {
    puts("why won\'t you make up your mind? the number he\'s thinking of is way cooler");
    return;
  }
  puts("see! all you had to do was let it happen. ");
  puts("but let\'s hope it wasn\'t just instant destiny. ");
  puts("\n=== LEVEL 3 ===");
  puts(
      "don\'t make kevin wait for one more year. give him the flag and set your reality in motion! "
      );
  printf("Flag: ");
  do {
    iVar1 = getc(stdin);
    if (iVar1 == -1) break;
  } while (iVar1 != 10);
  pcVar2 = fgets(local_88,0x80,stdin);
  if (pcVar2 == (char *)0x0) {
    puts("Input error.");
                    // WARNING: Subroutine does not return
    exit(0);
  }
  sVar3 = strcspn(local_88,"\n");
  local_88[sVar3] = '\0';
  iVar1 = FUN_00101240(local_88);
  if (iVar1 != 0) {
    puts(
        "RIGHT YOU ARE ! ! ! maybe you can also predict the release date of his next album, but that\'s for another challenge..."
        );
    return;
  }
  puts("new attempt, same old mistakes");
  return;
}



undefined8 FUN_001014c0(void)

{
  char *pcVar1;
  size_t sVar2;
  ulong uVar3;
  uint uVar4;
  ulong uVar5;
  char *__s;
  long lVar7;
  undefined8 *puVar8;
  undefined8 local_218 [2];
  char local_208 [512];
  ulong uVar6;
  
  puVar8 = local_218;
  puts("=== LEVEL 1 ===");
  __s = local_208;
  printf("kevin wants you to sing your heart out, it could be some music to walk home by: ");
  pcVar1 = fgets(__s,0x200,stdin);
  if (pcVar1 == (char *)0x0) {
    puts("Input error.");
  }
  else {
    sVar2 = strcspn(__s,"\n");
    uVar3 = 0x10;
    if (sVar2 < 0x11) {
      uVar3 = sVar2;
    }
    if (7 < (uint)uVar3) {
      uVar5 = 0;
      do {
        uVar4 = (int)uVar5 + 8;
        uVar6 = (ulong)uVar4;
        *(undefined8 *)((long)local_218 + uVar5) = *(undefined8 *)(__s + uVar5);
        uVar5 = uVar6;
      } while (uVar4 < ((uint)uVar3 & 0xfffffff8));
      puVar8 = (undefined8 *)((long)local_218 + uVar6);
      __s = __s + uVar6;
    }
    lVar7 = 0;
    if ((uVar3 & 4) != 0) {
      *(undefined4 *)puVar8 = *(undefined4 *)__s;
      lVar7 = 4;
    }
    if ((uVar3 & 2) != 0) {
      *(undefined2 *)((long)puVar8 + lVar7) = *(undefined2 *)(__s + lVar7);
      lVar7 = lVar7 + 2;
    }
    if ((uVar3 & 1) != 0) {
      *(char *)((long)puVar8 + lVar7) = __s[lVar7];
    }
    if (0xf < sVar2) {
      puts("okay okay maybe the sun\'s coming up.");
      FUN_00101340();
      return 1;
    }
    puts("maybe your song needs to be a full length song rather than a snippet");
  }
  return 0;
}



void _DT_FINI(void)

{
  return;
}
```
## Database Incursion    
After your legendary battle with the artist, the virtual world has returned, stretching around you in  
endless grids and flickering data, you find a rogue data terminal and on careful inspection, you find  
you’re able to inject rogue structured queries. Using this critical vulnerability, find a way to  
extract the hidden passcode.   


Challenge: https://databaseincursion.citadel.cryptonitemit.in  
### Solve  
**Flag:** ``



## BRATCHA
A clear chime rolls through the chamber and a new crest ignites on your badge – a quiet promotion. The  
outer ring is behind you. From here, the Citadel opens its inner systems, and the locks grow heavier  
because the keys are worth more. Your answers now carry more weight – and earn more in return. The  
citadel welcomes you to the inner climb.  

Near the gate to the next floor you come across a CAPTCHA verification test, but it has been covered by  
scratches on the decaying wall and misleading letters stopping you from finding the correct key, all to  
prove you’re human.  
### Solve
**Flag:** ``

## A Memory's a Heavy Burden


You now find yourself in the place where many climbers have been laid to rest. A cold wind moves  
through the temple grounds, carrying whispers of the departed. Stone lanterns and marble graves reflect  
Buddhist traditions, their shadows stretching across the frost-covered earth. 

The temple rests in the shadow of a very iconic mountain, quiet and imposing. Every detail in the image, the  
arrangement of the graves, the lanterns, and the lingering scent of incense, holds clues to its true location. You need to  
uncover the exact coordinates of where you are to move on from here.  


Note: round off coordinates to 3 decimal places.   


Flag format: citadel{XX.XXX_XXX.XXX}  
### Solve
**Flag:** `citadel{35.486_138.699}`
I located the spot on Google Maps Street View: it’s Mount Fuji with a Buddhist temple just to  
the south — coordinates **35.4856682, 138.6987152**.  
## Case sensitivity

You step into a constricted floor where every movement and operation is limited. Commands are few, space is tight, and options are restricted.

A guardian looms over the floor, its body shifting like liquid metal, enforcing these constraints. It watches your every move, daring you to make do with what you have and uncover the passcode to the next floor despite the restrictions.

Connection: ``nc chall_citadel.cryptonitemit.in 32770 ``

### Solve
**Flag:** `citadel{d34th_d035_n07_fr33_y0u_fr0m_7h3_gu17ar15t}`

Upon connecting, most commands are blocked. Attempts to use common commands like cat flag or print produce errors, with messages hinting those words are close to being allowed. environ also fails, but with a different error than forbidden words—implying the wordlist is case-sensitive.

Closer inspection reveals that the environment variable FLAG likely contains the flag, but needs to be accessed in a permitted way. The interpreter whitelist is found to allow several words—PRINT, ENVIRON, FLAG, lower, and exec—but only if matched case-sensitively.

Using these, a crafted input like execPRINTENVIRON.lower FLAG is accepted. This executes a print of the lowercased environment, from which the flag can be easily extracted.  
## Field day


Deep within the fortified citadel, ancient UNIVAC mainframes hum with classified transmissions. You have spent days infiltrating the Citadel's military grade communication defenses and manage to intercept a FIELDATA transmission encoded onto one of the first methods of storing data. However the data is trapped behind a peculiar digital representation of the FIELDATA encoding, different from the usual 6 bit pairing. Decode the 12 bit transmission to uncover the resistance's secret message.

Flag format: Wrap the decoded message with citadel{}

Data within "transmission.txt": ``010000010010010000000001000001000000100010000000000001000000010001000000010001000000000100000000001000000000010000010000010001000010000010000010100000010010100010000000001000100000000100000000010000010010010001000000001001000000000000010010001000000000010000010000100000010010100000000010001000000000010000010010010000000100000001000000``

### Solve
**Flag:** `citadel{r3b3ll10n$&BU1lt:0nH0p3}`

Solving this challenge involved converting 12-bit binary segments—each corresponding to a punched card column—into characters using the FIELDATA encoding scheme. Certain binary patterns acted as control codes, signaling when to switch between uppercase and lowercase.

To decode the data, the binary string was first split into 12-bit chunks. Each chunk was then matched to its equivalent character in the FIELDATA punched card table. Special patterns were handled to manage the case shifts accurately.

By implementing this logic in a Python script, the binary data was successfully decoded, ultimately revealing the flag.















