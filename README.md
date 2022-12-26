# Lifecraft
Life Simulation without a designated Player Character. You can select God, peasant or a king.

The project, my goal is to make a "zero player game", where the creatures are entities who interact, become hungry, thirsty, angry, bored, restless, happy, joyful and tired. They mate and have children. Children go through mixing of genes and genes directly affects characters physical and mental start state. I'm finding about how to finally create the genes and how to make them act like they should. Now they are like blocks of assembly, some instructions are glued together, like the action / instruction / conditional and value+parameters of the action. The genes build up the character bit by bit and affect the little neural network creature have.

struct Gene { byte action, word params[4], bool dominant, float value };

Item dynamics is much borrowed from Diablo, Adom and other great games. Game can be projected as a curses orthographic view, but the world is three dimensional. In practice the creatures mainly use only the ground layer of the map. Items are owned always by the world and only referenced to creatures.

struct Transform { vec3 pos, vec4 rot, vec3 euler } ; struct Target { idworld_entity, Rect location, char type_flags }; first bit = RADIAL, second bit = CREATURE ... struct Creature { transform t, stats s, body b, Target target, vec3 look_dir, int race }; struct Item { id holder == nullptr(ground), id* owner, uint16_t type, transform t } class Pool { ... } class CreaturePool extends Pool class ItemPool extends poool class StructurePool exteds pool class PropPool extends pool class DynamicPropPool extends pool class MapPool extends pool class World(){ std::vector<Pool*> p }

Creatures can communicate and they have ability to form relationships. Group of friends becomes a party. When a party thinks its good for it to settle down and start building a village, they will. Then the become villagers. If the village is large enough somebody with leader gene naturally rises to be a leader. Others have to confirm him/her as the leader.

If the leader thinks the village is ready to be a city state, it will become that. If the village is on friendly states territory the village will become property of that state and villagers become citizens of that state. If the village resides on enemy territory, it counts as a military camp.

About states. If one or more villages/towns/cities decides they should be a state, they will become one. I happens with the following mechanic: a messenger is sent from the village which decides to form an alliance to the nearest friendly village. They decide if they should form war, peace, alliance, or state. States can form unions. Forming a state is a big thing and the state leader is chosen.

tools being used: MinGW, SDL2 renderer, C++, k-di IDE, ncurses

Maybe thats enough for now :)
