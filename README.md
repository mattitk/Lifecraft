# Lifecraft
Life Simulation without a designated Player Character. You can select God, peasant or a king and switch role as you wish. Maybe some multiplayer or challenge modes could be added later.
I have been working on this project since 1999 and started it on QBasic.

The project, my goal is to make a "zero player game", where the creatures are entities who interact, become hungry, thirsty, angry, bored, restless, happy, joyful and tired. They mate and have children. Children go through mixing of genes and genes directly affects characters physical and mental start state. I'm finding about how to finally create the genes and how to make them act like they should. Now they are like blocks of assembly, some instructions are glued together, like the action / instruction / conditional and value+parameters of the action. The genes build up the character bit by bit and affect the little neural network creature have.

struct Gene { char base_pair[2], bool dominant };
struct State { uint64_t flags, int32_t state, vec3 pos, vec3 rot }
struct Action { string action_seq, Action(str, effects.. ), Check(str), Run(state) }
struct GeneSeq { std::vector<Gene> genes, Run -> return Action(params) }
InitGeneSequences();
struct Body_part { float hp, Float(HP, STR, DEX, PERCEPTION, SPEED, int current_animation, float animation_phase, Item *wield }
struct Body { std::vector<GeneSeq>, vec3 pos, vec3 rot, int race_a, int race_b, Body_part parts[16], float arcane_potential }
struct Spirit { String(FILENAME, NAME , HeardInput, Spatial surroundings, Float(MANA, REGEN, DANGER, SPIRITUAL_PRESENCE, vector<Spell> spells, vector<Skill> skills, Action, AI_Output last_ai_outputfloat AI_LEVEL, float LOS_DETAIL }
struct Creature { Body body, Spirit spirit, Targets, State, Jobs, Current_Job, Flags }

Item dynamics is much borrowed from Diablo, Adom and other great games. Game can be projected as a curses orthographic view, but the world is three dimensional. In practice the creatures mainly use only the ground layer of the map. Items are owned always by the world (IN A ITEM CONTAINER) and only referenced to creatures.

struct Transform { vec3 pos, vec4 rot, vec3 euler } ; struct Target { idworld_entity, Rect location, char type_flags }; first bit = RADIAL, second bit = CREATURE ...  }; 
struct Item { id holder = NULL, id owner = NULL, uint16_t type, transform t } class Pool { ... } class Pool extends Pool class StaticPool extends pool class WorldPool exteds pool class and DynamicPool extends pool class DynamicPropPool extends
pool class MapPool extends pool class World(){ std::vector<Pool*> p }

Creatures can communicate and they have ability to form relationships. Group of friends becomes a party. When a party thinks its good for it to settle down and start building a village, they will. Then the become villagers. If the village is large enough somebody with leader gene naturally rises to be a leader. Others have to confirm him/her as the leader.

If the leader thinks the village is ready to be a city state, it will become that. If the village is on friendly states territory the village will become property of that state and villagers become citizens of that state. If the village resides on enemy territory, it counts as a military camp.

About states. If one or more villages/towns/cities decides they should be a state, they will become one. I happens with the following mechanic: a messenger is sent from the village which decides to form an alliance to the nearest friendly village. They decide if they should form war, peace, alliance, or state. States can form unions. Forming a state is a big thing and the state leader is chosen.

tools being used: MinGW, SDL2 renderer, C++, k-di IDE, ncurses

Maybe thats enough for now :)

