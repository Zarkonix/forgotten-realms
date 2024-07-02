class NPC:
    def __init__(self, name, description):
        self.name = name
        self.description = description

    def introduce(self):
        return f"Name: {self.name}\nDescription: {self.description}"

aribeth = NPC("Aribeth De'Tylmarande", "A paladin of Tyr who is determined to uncover the truth.")
volo = NPC("Volo Geddarm", "A famous bard and author who loves to tell tales.")

print(aribeth.introduce())
print(volo.introduce())
Encounter Setup
python
class Encounter:
    def __init__(self, location, enemies):
        self.location = location
        self.enemies = enemies

    def describe(self):
        return f"Location: {self.location}\nEnemies: {', '.join(self.enemies)}"

ambush = Encounter("Dark Alley", ["3 Thugs"])
haunted_warehouse = Encounter("Haunted Warehouse", ["Ghost", "2 Wraiths"])
sewer_lair = Encounter("Sewer Lair", ["Xathros the Necromancer", "5 Zombies"])

print(ambush.describe())
print(haunted_warehouse.describe())
print(sewer_lair.describe())
Simple Battle System
python
import random

class Character:
    def __init__(self, name, health, attack_power):
        self.name = name
        self.health = health
        self.attack_power = attack_power

    def attack(self, other):
        damage = random.randint(1, self.attack_power)
        other.health -= damage
        return damage

class Player(Character):
    pass

class Enemy(Character):
    pass

player = Player("Hero", 100, 20)
thug = Enemy("Thug", 50, 10)

print(f"Battle Start!\n{player.name} vs {thug.name}")

while player.health > 0 and thug.health > 0:
    damage = player.attack(thug)
    print(f"{player.name} attacks {thug.name} for {damage} damage.")
    if thug.health <= 0:
        print(f"{thug.name} is defeated!")
        break

    damage = thug.attack(player)
    print(f"{thug.name} attacks {player.name} for {damage} damage.")
    if player.health <= 0:
        print(f"{player.name} is defeated!")
        break

print("Battle Over")
