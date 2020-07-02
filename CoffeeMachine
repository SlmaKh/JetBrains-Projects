class CoffeeMachine:
    def __init__(self, water, milk, coffe_beans, cups, money):
        self.water = water
        self.milk = milk
        self.coffee_beans = coffe_beans
        self.cups = cups
        self.money = money
        self.set_state("action")

    def set_state(self, state):
        self.state = state
        if state == "action":
            print("Write action (buy, fill, take, remaining, exit):")
        elif state == "fill_water":
            print("Write how many ml of water do you want to add:")
        elif state == "fill_milk":
            print("Write how many ml of milk do you want to add:")
        elif state == "fill_coffee_beans":
            print("Write how many grams of coffee beans do you want to add:")
        elif state == "fill_cups":
            print("Write how many disposable cups of coffee do you want to add:")
        elif state == "buy":
            print("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:")

    def change_state(self, user_input):
        if self.state == "action":
            if user_input == "fill":
               self.set_state("fill_water")
            else:
                self.set_state(user_input)

    def interact(self, user_input):
        if user_input == "exit":
            return user_input
        if self.state == "action":
            self.change_state(user_input)
            if self.state == "remaining":
                self.print_remaining()
                self.set_state("action")
            elif self.state == "take":
                self.take()
                self.set_state("action")
        elif self.state == "buy":
            self.buy(user_input)
            self.set_state("action")
        elif self.state == "fill_water":
            self.fill_water(user_input)
            self.set_state("fill_milk")
        elif self.state == "fill_milk":
            self.fill_milk(user_input)
            self.set_state("fill_coffee_beans")
        elif self.state == "fill_coffee_beans":
            self.fill_coffee_beans(user_input)
            self.set_state("fill_cups")
        elif self.state == "fill_cups":
            self.fill_cups(user_input)
            self.set_state("action")

    def take(self):
        print("I gave you ", self.money)
        self.money = 0

    def fill_water(self,water_added):
        self.water = self.water + int(water_added)

    def fill_milk(self, milk_added):
        self.milk = self.milk +  int(milk_added)

    def fill_coffee_beans(self, coffee_beans_added):
        self.coffee_beans = self.coffee_beans + int(coffee_beans_added)

    def fill_cups(self, cups_added):
        self.cups = self.cups + int(cups_added)

    def buy(self, type):
        if type == "1":
            if self.check_resources(250, 0, 16):
                print("I have enough resources, making you a coffee!")
                self.consume(250, 0, 16, 4)
        elif type == "2":
            if self.check_resources(350, 75, 20):
                print("I have enough resources, making you a coffee!")
                self.consume(350, 75, 20, 7)
        elif type == "3":
            if self.check_resources(200, 100, 12):
                print("I have enough resources, making you a coffee!")
                self.consume(200, 100, 12, 6)
        #self.set_state("action")

    def check_resources(self, w, m, cb):
        enough = True
        if w > self.water:
            print("Sorry, not enough water!")
            enough = False
        if m > self.milk:
            print("Sorry, not enough milk!")
            enough = False
        if cb > self.coffee_beans:
            print("Sorry, not enough coffee beans!")
            enough = False
        if self.cups == 0:
            print("Sorry, not enough cups!")
            enough = False
        return enough

    def consume(self, w, m, cb, cost):
        self.water -= w
        self.milk -= m
        self.coffee_beans -= cb
        self.money += cost
        self.cups -= 1

    def print_remaining(self):
        print("The coffee machine has:")
        print("{} of water".format(self.water))
        print("{} of milk".format(self.milk))
        print("{} of coffee beans".format(self.coffee_beans))
        print("{} of disposable cups".format(self.cups))
        print("${} of money".format(self.money))


cf = CoffeeMachine(400, 540, 120, 9,550)
while True:
    inpt = input()
    reaction = cf.interact(inpt)
    if reaction == "exit":
        break






