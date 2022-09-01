# Kumite - A Sparring Video Game

This design document for *Kumite* is scoped for a minimum viable product. There will be features lacking that would be present in a more polished version. I've left out any description of the game's aesthetics because I want to focus on gameplay systems and not get too ahead of myself.

![Fight Photo](/images/screenshot-spar.jpg)

## Overview

Inspired by *Karate Tournament*, *Bushido Blade*, and *Virtua Fighter*, *Kumite* is a 3D sparring game that seeks to refine the pre-*Street Fighter II* design of early fighting games by returning to a more deliberate, tactical style of gameplay. 
Players fight in flat 3D arenas, with health points and a timer, fighting traditional best-of-three rounds.

### Character Select

There are no unique characters in *Kumite*. Players select their gi colour to distinguish themselves in a match, but characters will otherwise appear identical.

### Time Out

If the timer runs out, the player with the most health will win the round. If both players' health is tied, the round counts as a draw, and a round will be awarded to both players. Games cannot end as a draw and if the final match draws, extra rounds are played until there is a single winner.

## Controls

*Kumite* is played using a Joystick ![Joystick Up](/images/c_8.gif) and three buttons: Punch ![Button A](/images/c_a.gif), Kick ![Button B](/images/c_b.gif), and Evade ![Button C](/images/c_c.gif).

Command (when facing right) | Motion
------------ | -------------
![Button A](/images/c_a.gif) | Punch
![Button B](/images/c_b.gif) | Kick
![Button C](/images/c_c.gif) | Evade
![Button A](/images/c_a.gif)+![Button B](/images/c_b.gif) | Power Attack
![Button A](/images/c_a.gif)+![Button C](/images/c_c.gif) or ![Button B](/images/c_b.gif)+![Button C](/images/c_c.gif) | Circular Attack
![Joystick Up](/images/c_8.gif) (hold) | High Stance
![Joystick Down](/images/c_2.gif) (hold) | Low Stance
![Joystick Right](/images/c_6.gif)![Joystick Right](/images/c_6.gif) or ![Joystick Right](/images/c_6.gif)+![Button C](/images/c_c.gif) | Dash Forward
![Joystick Left](/images/c_4.gif)![Joystick Left](/images/c_4.gif) or ![Joystick Left](/images/c_4.gif)+![Button C](/images/c_c.gif) | Dash Backward

### Stances

Critical to combat in *Kumite* is the Stance system. Similar to games like *Nidhogg*, the player can hold ![Joystick Up](/images/c_8.gif) or ![Joystick Down](/images/c_2.gif) on the joystick to switch to High or Low Stances. This changes what height of attacks will be used and what kinds of moves the player can block against. When the joystick is neutral, the player is in Mid Stance. If an attack is active for multiple frames, as long as the first frame is correctly blocked, the defending player can switch out of that stance without getting hit. Most moves in fighting games are active for 1 or 2 frames. Switching stances can only be done when in the Standing state.

### Blocking

Blocking in *Kumite* is automatic and will succeed if the player is not attacking, dashing, or evading while in the correct stance. Kumite does not have chip damage. If one player holds the joystick ![Joystick Up](/images/c_8.gif) to strike high, the other player must be holding the joystick ![Joystick Up](/images/c_8.gif) in the high stance to block the strike.

After a successful block the blocker will have a frame advantage if a normal attack was blocked, and a frame disadvantage if a Power Attack or Circular Attack was blocked.

### Punches and Kicks

Punch ![Button A](/images/c_a.gif) and Kick ![Button B](/images/c_b.gif). Punches have a shorter range but a shorter startup time, while kicks have a greater range but have a longer startup time. Hitting the enemy with the joystick in neutral will produce a Middle attack, while holding ![Joystick Up](/images/c_8.gif) while attacking strikes High, and holding ![Joystick Down](/images/c_2.gif) while attacking strikes Low. Striking a standing opponent will do 1 point of damage, while striking an enemy from the side or behind will do 1.5 points of damage. 

### Followup Attacks

*Kumite* does not have a conventional combo system. Rather, successful normal attacks can follow up with one other normal attack, in any of the three Stances. During the followup the defending player can evade or switch stances to block the second attack, even if they were hit by the first move. If both attacks hit the enemy, it will produce a Knockdown. There is a brief window of a few frames for which a second attack will count as a followup, that allows players to delay their strike. 

### Power Attacks

Power Attacks are performed by pressing Punch and Kick together (![Button A](/images/c_a.gif)+![Button B](/images/c_b.gif)). Power Attacks are slower strikes with long windups that Knock Down and do 3 points of damage. Power Attacks can be performed in each of the stances. Like in *Tekken* players can input a dash command to cancel out of the Power Attack windup and return to Standing state.

### Circular Attacks

Pressing Punch and Evade or Kick and Evade (![Button A](/images/c_a.gif)+![Button C](/images/c_c.gif) or ![Button B](/images/c_b.gif)+![Button C](/images/c_c.gif)) will perform a Circular Attack. Circular Attacks travel through the foreground and background, hitting opponents that the attacker is not tracking. Circular Attacks have a medium windup time. They are faster than Power Attacks but slower than Kicks. Circular Attacks are primarily to hit a player that Evades predictably, but can also be used normally as a medium strength attack. Performing a Circular Attack puts the player in Mid stance and counts as a Mid attack.

Landing a Circular Attack produces a Knockdown and deals 2 points of damage.

### Evade

Evade ![Button C](/images/c_c.gif) will be covered in the Movement section.

### Input Buffer

Input buffers function as normal in other fighting games. In *Virtua Fighter 5* the input buffer is 10 frames. In *King of Fighters* the input buffer is 4 frames for normal moves and 13 frames for special/super moves. In ArcSys games, if a button is held down, the game repeats the button pressed for 3 frames. *Kumite* will have one of these implementations.

### Button Priority

Button priority is ![Button C](/images/c_c.gif)>![Button B](/images/c_b.gif)>![Button A](/images/c_a.gif). So pressing all three buttons will perform a Circular Attack.

## Movement

### Walking

Players can walk back or forward by holding the Joystick ![Joystick Left](/images/c_4.gif) or ![Joystick Right](/images/c_6.gif). When walking normally, players will be in Mid Stance. Holding a diagonal input (![Joystick Upleft](/images/c_7.gif)![Joystick Upright](/images/c_9.gif)![Joystick Downright](/images/c_3.gif)![Joystick Downleft](/images/c_1.gif)) allows the player to move back or forward while maintaining a high or low stance.

### Dashing

Players can dash forward or back with a double forward or backward tap of the Joystick (![Joystick Left](/images/c_4.gif)![Joystick Left](/images/c_4.gif) and ![Joystick Right](/images/c_6.gif)![Joystick Right](/images/c_6.gif)), or by tapping forward or back while Evading (![Joystick Left](/images/c_4.gif)+![Button C](/images/c_c.gif)and![Joystick Right](/images/c_6.gif)+![Button C](/images/c_c.gif)). when dashing, players cannot block, and any attack that hits them will perform a Knockdown. Forward dashes can be canceled by tapping ![Joystick Left](/images/c_4.gif) on the joystick to control spacing and quickly block. Back dashes can not be canceled. Back dashes should have some invincibility frames. Players cannot Attack or Evade during a dash. Back dashes have a recovery window, while forward dashes do not.

### Evading

Evading ![Button C](/images/c_c.gif) allows players to move in a sideways direction clockwise or counterclockwise into the foreground or background. This allows players to escape the opponent’s attack and expose their side or back, or to change positions around the ring. Tapping ![Button C](/images/c_c.gif) will dodge into the background, and tapping the Joystick ![Joystick Up](/images/c_8.gif) or ![Joystick Down](/images/c_2.gif) alongside ![Button C](/images/c_c.gif) will dash into the background or foreground. 

Players can be hit by a Circular Attack during an Evade. The result of an Evade is determined by the opponent's action when the Evade occurs. Aside from Circular Attacks, if the player inputs an Evade *after* the opponent has initiated an attack, the Evade will be successful. If the player inputs an Evade *before* the opponent initiates an attack, the Evade will fail and result in a hit.

Evasion is a powerful defence tool in *Kumite*, since guessing which stance to block has only a 33% chance of success compared to 50% in most fighters.

### A note on Jumping and Crouching

*Kumite* has no Jumping or Crouching. This is not a title with an air game, overheads or combos, and ducking under and jumping over attacks are not necessary due to the stance blocking system. In low stance, the player will go lower to the ground, but not enough to avoid high attacks. Landing some Power Attacks may launch the defending player in the air.

## Attacks

### Attack Phases

Attack phases function as they do in other fighters, with an execution phase, an active phase, and a recovery phase. Attacks take significantly longer to perform compared to other fighters, due to *Kumite*’s high damage and focus on reading opponent movement and striking at the right opportunity. The frame data from *Karate Tournament* and the *Samurai Shodown* series would make for good references. 

### Knockback

Ground control plays a heavy role in *Kumite*. Attacks cause a large and equal amount of knockback whether they are successful or blocked. In *Karate Tournament*, the player can be pushed out of the arena by knockback from default position in 6 normal hits or 3 power hits, assuming they don’t move. So Power Attacks cause double the knockback of normal attacks. They would also have, on average, double the recovery time.  Knockback will have to be examined against punches/kicks, and a decision will have to be made whether blocking players will be able to respond with an attack, if they have frame advantage.

### Attack Trades

If both players trade:
- The attack that does the higher damage wins
- If the damage is equal, neither player will receive damage. A visual indicator will appear to let players know that the trade was equal, and both players will be pushed back the amount of a Power Attack. Players cannot be knocked off the arena in this way and will instead land one step away from the edge.

### Attack Tracking

Tracking is a character lining up their attacks to hit an opponent that has adjusted their position from an Evade. Like in *Virtua Fighter*, If one player evades to the side and hasn't pressed any buttons, the other player's hits won't track, and will instead land on the wrong axis. If the defending player presses a button, the attack will track and they will get hit.

## States

### Standing

Standard state. This is the only state where the player can block, attack, switch stances or evade.

### Knocked Down

Players enter the Knockdown state after being hit by an attack and its followup attack, a Power Attack, or from falling off the arena. Players are also Knocked Down after losing their last point of health at the end of a round. In this state the player cannot be hit, and both players are reset to their default positions in the middle of the arena. Knockdowns exist to moderate the pacing of the match, to allow players to register what caused the Knockdown, and to remove the wakeup game from the fighting design template.

### Ring Out

If a player falls outside of the ring, they will suffer a Knockdown and take 2 points of damage. Only one character can take damage from ringing out at a time. Players cannot walk off the ring and must dash, evade, or get pushed back or knocked off the ring. 

Damage does not stack if a player is hit and knocked out of the ring. Instead the higher source of damage will be dealt. So if a player is knocked out of the ring by a normal attack, they will take 2 points of damage. If they are knocked out by a Power Attack they will take 3 points of damage.

## Future Concepts

In the future a "match structure" section will be needed, outlining pre-match and post-match gameplay. Also more on the intended player experience, using examples from other games. *Fighters Destiny* has a similar point system and could point to future gameplay expansion. Other possible ideas include:

- Multiple characters with unique abilities
- Pre-match movement like in *Dead Or Alive*

## References

- [Virtua Fighter Wiki](https://virtuafighter.com/wiki/index/)
- [HG101 Article on The Karate Tournament](http://www.hardcoregaming101.net/chatan-yarakuu-shanku/)
- [HG101 Article on Fighters Destiny](http://www.hardcoregaming101.net/fighters-destiny/)
