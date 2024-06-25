# floor-mopping-robot
import time

class MoppingRobot:
    def __init__(self):
        self.position = [0, 0]  # Starting position (x, y)
        self.direction = 'N'  # Starting direction (N, E, S, W)
    
    def move_forward(self, distance):
        if self.direction == 'N':
            self.position[1] += distance
        elif self.direction == 'E':
            self.position[0] += distance
        elif self.direction == 'S':
            self.position[1] -= distance
        elif self.direction == 'W':
            self.position[0] -= distance
        print(f"Moved {distance} meters {self.direction}. New position: {self.position}")
    
    def move_backward(self, distance):
        if self.direction == 'N':
            self.position[1] -= distance
        elif self.direction == 'E':
            self.position[0] -= distance
        elif self.direction == 'S':
            self.position[1] += distance
        elif self.direction == 'W':
            self.position[0] += distance
        print(f"Moved {distance} meters backward. New position: {self.position}")
    
    def turn_right(self):
        directions = ['N', 'E', 'S', 'W']
        current_index = directions.index(self.direction)
        self.direction = directions[(current_index + 1) % 4]
        print(f"Turned right. New direction: {self.direction}")
    
    def turn_left(self):
        directions = ['N', 'E', 'S', 'W']
        current_index = directions.index(self.direction)
        self.direction = directions[(current_index - 1) % 4]
        print(f"Turned left. New direction: {self.direction}")
    
    def mop(self):
        print("Mopping the floor...")
        time.sleep(1)  # Simulate mopping time

def main():
    robot = MoppingRobot()
    distance = 5
    for _ in range(4):  # Repeat the pattern 4 times
        robot.move_forward(distance)
        robot.move_backward(distance)
        robot.turn_right()
        robot.move_forward(distance)
        robot.mop()
        robot.turn_left()
        robot.move_forward(distance)
        robot.mop()

if __name__ == "__main__":
    main()
