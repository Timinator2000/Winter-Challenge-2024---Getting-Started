# Initial Source Code

```python
import sys
import math

# Grow and multiply your organisms to end up larger than your opponent.

# width: columns in the game grid
# height: rows in the game grid
width, height = [int(i) for i in input().split()]

# game loop
while True:
    entity_count = int(input())
    for i in range(entity_count):
        inputs = input().split()
        x = int(inputs[0])
        y = int(inputs[1])  # grid coordinate
        _type = inputs[2]  # WALL, ROOT, BASIC, TENTACLE, HARVESTER, SPORER, A, B, C, D
        owner = int(inputs[3])  # 1 if your organ, 0 if enemy organ, -1 if neither
        organ_id = int(inputs[4])  # id of this entity if it's an organ, 0 otherwise
        organ_dir = inputs[5]  # N,E,S,W or X if not an organ
        organ_parent_id = int(inputs[6])
        organ_root_id = int(inputs[7])
    # my_d: your protein stock
    my_a, my_b, my_c, my_d = [int(i) for i in input().split()]
    # opp_d: opponent's protein stock
    opp_a, opp_b, opp_c, opp_d = [int(i) for i in input().split()]
    required_actions_count = int(input())  # your number of organisms, output an action for each one in any order
    for i in range(required_actions_count):

        # Write an action using print
        # To debug: print("Debug messages...", file=sys.stderr, flush=True)

        print("WAIT")
```


# Intial Reorganization

```
import sys
import math


GLOBAL_DEBUG = True


def debug(*args):
    if GLOBAL_DEBUG:
        print(args, file=sys.stderr, flush=True)


class Entity():

    def __init__(self, data: str):

        inputs = data.split()
        self.x = int(inputs[0])
        self.y = int(inputs[1])  # grid coordinate
        self.type = inputs[2]  # WALL, ROOT, BASIC, TENTACLE, HARVESTER, SPORER, A, B, C, D
        self.owner = int(inputs[3])  # 1 if your organ, 0 if enemy organ, -1 if neither
        self.organ_id = int(inputs[4])  # id of this entity if it's an organ, 0 otherwise
        self.organ_dir = inputs[5]  # N,E,S,W or X if not an organ
        self.organ_parent_id = int(inputs[6])
        self.organ_root_id = int(inputs[7])



class WinterChallenge2024():

    def __init__(self):

        self.turn = 0
        self.width, self.height = [int(i) for i in input().split()]
        self.entities = []
        self.my_proteins = {'A': 0, 'B': 0, 'C': 0, 'D': 0}
        self.opp_proteins = {'A': 0, 'B': 0, 'C': 0, 'D': 0}


    def update(self):

        self.entities = []
        for _ in range(int(input())):
            self.entities.append(Entity(input()))

        for amount, protein_type in zip([int(i) for i in input().split()], 'ABCD'):
            self.my_proteins[protein_type] = amount

        for amount, protein_type in zip([int(i) for i in input().split()], 'ABCD'):
            self.opp_proteins[protein_type] = amount

        self.required_actions_count = int(input())  # your number of organisms, output an action for each one in any order


    def play(self):

        while True:
            self.turn += 1
            self.update()

            for _ in range(self.required_actions_count):

                # In Wood 4, my ROOT always appears to be on the left side of the board. 
                print(f'GROW {1} {self.width-1} {2} BASIC')



game = WinterChallenge2024()
game.play()
```


# Wood 4 - Always Target Closest Protein

