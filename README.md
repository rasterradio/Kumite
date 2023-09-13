# Shotokan Dojo - A Sparring Video Game

This design document for *Shotokan Dojo* is scoped for a minimum viable product. Features are lacking that would be present in a more polished version. I've left out details of the game's aesthetics because I want to focus on gameplay and not get ahead of myself.

![Fight Photo](/images/screenshot-spar.jpg)

## Overview

Inspired by *Karate Tournament*, *Bushido Blade*, and *Virtua Fighter*, *Shotokan Dojo* is a 3D sparring game that seeks to refine the pre-*Street Fighter II* design of primordial fighting games with more deliberate, tactical gameplay. Sidestep your opponent, predict their move, and strike. Earn the stripes on your gi. Respect is earned, not given.

Players fight in flat 3D arenas, with health points and a timer, fighting best-of-three rounds.

### Character Select

There are no unique characters in *Shotokan Dojo*. Players select their gi colour to distinguish themselves in a match.

### Health

Health is binary, with a low total of hit points such as six or eight. Moves have clear damage results and players can tell at a glance how many mistakes they can afford to make.

![Fantasy Strike HUD](/images/fantasy_strike_health_bar.JPG)

<sub>A health bar in *Fantasy Strike*. At a glance, players can measure how much damage an attack deals and how many hits they can take.</sub>

### Time Out

If the timer runs out, the player with the most health wins the round. If both players' health is tied, the round counts as a draw, and a round will be awarded to both players. Games can't end with a draw and if the final match draws, extra rounds are played until there is a single winner.

## Controls

*Shotokan Dojo* is played using a Joystick ![Joystick Up](/images/c_8.gif) and three buttons: Punch ![Button A](/images/c_a.gif), Kick ![Button B](/images/c_b.gif), and Evade ![Button C](/images/c_c.gif).

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

Crucial to combat in *Shotokan Dojo* is the Stance system. Like in *Nidhogg*, the player can hold ![Joystick Up](/images/c_8.gif) or ![Joystick Down](/images/c_2.gif) to switch to the respective High or Low Stance. When the joystick is neutral, the player is in Mid Stance. Stances change what height of attacks are used and what moves the player can block. Switching stances can only be done in the Standing state.

### Blocking

Blocking in *Shotokan Dojo* is automatic and will succeed if the player is not attacking, dashing, or evading while in the correct stance. If the attacker inputs ![Joystick Up](/images/c_8.gif) to strike high, the defender must also input ![Joystick Up](/images/c_8.gif) in the high stance to block the strike.

The defender will have a frame advantage if a normal attack was blocked, and a frame disadvantage if a Power Attack or Circular Attack was blocked.

If an attack is active for multiple frames, as long as the first frame is blocked, the defender will stay in the correct stance during the attack regardless of joystick input.

Shotokan Dojo doesn't have chip damage when blocking.

### Punches and Kicks

Punch ![Button A](/images/c_a.gif) and Kick ![Button B](/images/c_b.gif). Punches have a shorter range but a shorter startup time, while kicks have a greater range but a longer startup time. Attacking with the joystick in neutral performs a Mid attack, holding ![Joystick Up](/images/c_8.gif) while attacking strikes High, and holding ![Joystick Down](/images/c_2.gif) while attacking strikes Low. Striking a standing opponent does 1 point of damage. 

### Followup Attacks

*Shotokan Dojo* does not have a conventional combo system. Rather, successful normal attacks can be followed up with another normal attack, in any Stance. During the Followup the defender can Evade or switch stances to block the second attack, even if they were hit by the first move. If both attacks land, the defender will be Knocked Down. There is a brief window where a second attack counts as a Followup, letting players delay their strike. 

### Power Attacks

Power Attacks are performed by pressing Punch and Kick together (![Button A](/images/c_a.gif)+![Button B](/images/c_b.gif)). Power Attacks are slow strikes with long windups that Knockdown and do 3 points of damage. Power Attacks can be performed in each stance. Like in *Tekken*, players can input a dash to cancel out of the Power Attack startup and return to the Standing state.

### Circular Attacks

Pressing Punch and Evade or Kick and Evade (![Button A](/images/c_a.gif)+![Button C](/images/c_c.gif) or ![Button B](/images/c_b.gif)+![Button C](/images/c_c.gif)) will perform a Circular Attack. Circular Attacks travel through the foreground and background, hitting opponents that the attacker is not tracking on the Z-axis. Circular Attacks are faster than Power Attacks but slower than Kicks. Circular Attacks punish Evading opponents, but can also strike non-Evading enemies. Performing a Circular Attack puts the player in Mid stance and counts as a Mid attack.

Landing a Circular Attack produces a Knockdown and deals 2 points of damage.

### Evade

Evading ![Button C](/images/c_c.gif) is covered in the Movement section.

### Input Buffer

The Input buffer functions like other fighting games. In *Virtua Fighter 5* the input buffer is 10 frames. In *King of Fighters* the input buffer is 4 frames for normal moves and 13 frames for special/super moves. In ArcSys games, if a button is held down, the game repeats the pressed button for 3 frames. *Shotokan Dojo* will have one of these implementations.

### Button Priority

Button priority is ![Button C](/images/c_c.gif)>![Button B](/images/c_b.gif)>![Button A](/images/c_a.gif). So pressing all three buttons will perform a Circular Attack.

## Movement

### Walking

Players can walk back or forward by holding ![Joystick Left](/images/c_4.gif) or ![Joystick Right](/images/c_6.gif). When walking with ![Joystick Left](/images/c_4.gif) or ![Joystick Right](/images/c_6.gif), players will be in Mid Stance. Holding a diagonal input (![Joystick Upleft](/images/c_7.gif)![Joystick Upright](/images/c_9.gif)![Joystick Downright](/images/c_3.gif)![Joystick Downleft](/images/c_1.gif)) lets players move back or forward while maintaining a high or low stance. Walking into the opponent will push them.

### Dashing

Players can dash forward or back with a double forward or backward tap of the Joystick (![Joystick Left](/images/c_4.gif)![Joystick Left](/images/c_4.gif) and ![Joystick Right](/images/c_6.gif)![Joystick Right](/images/c_6.gif)), or by tapping forward or back and the Evade button (![Joystick Left](/images/c_4.gif)+![Button C](/images/c_c.gif) and ![Joystick Right](/images/c_6.gif)+![Button C](/images/c_c.gif)). When dashing, players can't block, and any attack that hits them will perform a Knockdown. Forward dashes can be canceled by tapping the opposite direction on the joystick to control spacing and quickly block. Back dashes can not be canceled but carry some invincibility frames. Back dashes have a recovery window, while forward dashes do not. Players can't Attack or Evade during a dash. Dashing into the opponent will push them.

### Evading

Evading ![Button C](/images/c_c.gif) lets players dodge clockwise or counterclockwise into the foreground or background. Players can Evade to avoid attacks and expose the side or back of the opponent, and maneuver around the ring. Tapping ![Button C](/images/c_c.gif) will dodge into the background, and tapping ![Joystick Up](/images/c_8.gif) or ![Joystick Down](/images/c_2.gif) alongside ![Button C](/images/c_c.gif) will dash into the background or foreground. 

Players can be hit by a Circular Attack during an Evade. The result of an Evade is determined by the opponent's action when the Evade occurs. Aside from Circular Attacks, if the player inputs an Evade *after* the opponent starts an attack, the Evade will succeed. If the player inputs an Evade *before* the opponent initiates an attack, the Evade will fail and result in a hit.

Evasion is a powerful defence tool in *Shotokan Dojo*. Guessing which stance to block has only a 33% chance of success compared to 50% in other fighters. Evades are more reliable but have more precise timings and can be punished with Circular Attacks.

![Tekken evade](/images/tekken_evade.gif)

<sub>A player evading multiple times in *Tekken*. Note that the opponent isn't tracking the player on the Z-axis. Attacks won't line up until the evading player presses a button.</sub>

### A note on Jumping and Crouching

*Shotokan Dojo* has no Jumping or Crouching. This is not a title with an air game, overheads or complex combos. Ducking under and jumping over attacks are unnecessary due to the Stance system. In the Low stance, the player will go lower to the ground, but not enough to avoid High attacks. Knockdowns launch the player into the air, but the effect is for show and not indicative of a juggling opportunity.

## Attacks

### Attack Phases

Attack phases function like other fighters, with an execution phase, an active phase, and a recovery phase. Attacks take longer to perform than most 3D fighters, due to *Shotokan Dojo*’s high damage and focus on reading the opponent's movement and striking at the right opportunity. The frame data from *Karate Tournament* and the *Samurai Shodown* series would make for helpful references. 

### Knockback

Ground control plays an important role in *Shotokan Dojo*. Attacks cause equal amounts of knockback whether they succeed or are blocked. In *Karate Tournament*, players are pushed out of the arena by knockback from the starting position in 6 normal hits or 3 power hits. So Power Attacks cause double the knockback of normal attacks. They also have double the recovery time. I'll need to weigh Knockbacks against punches and kicks, and decide to what extent defending players will have frame advantage when blocking.

### Attack Trades

If both players trade:
- The attack that does the higher damage wins
- If the damage is equal, neither player will receive damage. A visual indicator will let players know that the trade was equal, and both players will be pushed back the amount of a Power Attack. Players can't be knocked off the arena in this way and instead will land one step away from the edge.

### Attack Tracking

Tracking is a character lining up their attacks on the Z-axis to hit an opponent that has adjusted their position from an Evade. Like in *Virtua Fighter*, If one player evades to the side and hasn't pressed any buttons, the other player's hits won't track, and will instead whiff. If the defending player presses any button, the attack will track and they will get hit. The attack will also track if the player switches out of mid stance to high or low stance, but not from high or low stance into mid.

## States

### Standing

Standard state. This is the only state where the player can block, attack, switch stances or evade.

### Knocked Down

Players enter the Knockdown state when hit by an attack and its Followup Attack, a Power Attack, or from falling out of the arena. Players are also Knocked Down after losing their last health point at the end of a round. In this state the player cannot be hit, and both players return to their starting positions in the middle of the arena. While one player is Knocked Down, the attacking player can continue to move. Knockdowns moderate the pacing of the match. They let players reflect on what caused the Knockdown. And by resetting both players to neutral, Shotokan Dojo cuts the Wakeup Game from the fighting design template.

### Ring Out

If a player falls outside of the ring, they will suffer a Knockdown and take 2 points of damage. Only one character can be damaged from ringing out at a time. If both players Ring Out, whichever player hits the ground first will take damage. Players can't walk off the ring and must dash, evade, or get pushed back or knocked off the ring. 

Damage does not stack if a player is hit and knocked out of the ring. Instead, damage is only dealt from the more powerful source. So if a player is Ringed Out by a normal attack, they will only take 2 points of damage from the Ring Out. If they are Ringed Out by a Power Attack they will only take 3 points of damage from the Power Attack.

### Round Start

At the start of each round, before the battle begins, players get a few seconds to move freely around the arena. During this time, players can walk forward and back, dash, Evade, and change stance. Players cannot attack.

## Future Concepts

*Fighters Destiny* has a similar point system and could point to future gameplay expansion. Other possible ideas include:

- Multiple characters with distinct abilities
- Determine player distance at the start of the match. What options are available to players and how much do they need to move for other options to open/close?
- Figure out what exactly the defender can do while the attacker is executing a Followup Attack. Should they be able to Evade?
- More example images

## References

- [Virtua Fighter Wiki](https://virtuafighter.com/wiki/index/)
- [HG101 Article on The Karate Tournament](http://www.hardcoregaming101.net/chatan-yarakuu-shanku/)
- [HG101 Article on Fighters Destiny](http://www.hardcoregaming101.net/fighters-destiny/)
