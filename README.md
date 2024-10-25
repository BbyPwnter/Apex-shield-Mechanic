class Shield:
    # Saving values to use later in damaged method
    def __init__(self,life,shields):
        self.life = life
        self.shields = shields
        # Takes damage and hits shield first
    def damaged(self,damage):
        # If shields is still up stay in this while loop
        while  self.shields > 0:
            # Checking to see if shields can tank all the damage
            if damage < self.shields:
                self.shields -= damage
                print(f"you're shield has been damaged: Health:[{self.life}] Shield:[{self.shields}]")
                break
                # Checking to see if damage is enough to deplete shields
            if damage >= self.shields:
                damage -= self.shields
                self.shields = 0
                # Shield def cracked
                print(f"you're shield is cracked!!!!")
                # Displays when shield just so happens to break without health being lost
                if self.shields == 0 and damage == 0:
                    print(f"Snake watch it!!!. Health:[{self.life}], Shields:[{self.shields}]")
                break
        # Breaks from while loop if shield is broken
        if self.life > 0 and damage > 0 and self.shields == 0:
            # Checks to see if shield is depleted and also if damage is enough to kill snake
                self.life -= damage
                damage = 0
            # Checks to see if life still has health left
                if self.life > 0:
                    print(f"Yo im being dead ass watch your Health!:[{self.life}] Shields:[{self.shields}]")
        if damage >= self.life:
            # Snake dies
            self.life = 0
            print('Snake?!.... SNAKE!!!!!')

my_shield = Shield(100,60)
my_shield.damaged(60)
