# Tank Stars

### Welcome to our Tank Stars Game!

# Introduction

The following showcases glimpse of a clone of the mobile game ‘Tank Stars’, recreated using LibGdx and Box2D Physics Engine, employing important OOPs such as:

- Inheritance & Interfaces
- Encapsulation
- Polymorphism
- Abstraction
- JUnit Testing
- Serialisation
- Design Patterns
- Exception Handling

# Game Play

## Main Menu Screen

![Initial_Page.png](https://github.com/UtsvGrg/TankStars-GameClone/blob/main/Initial%20Page.png)
<image>

## Tank Selection Screen

The Game comprises of 4 tanks, each having one special attack.

![User_Page.png](https://github.com/UtsvGrg/TankStars-GameClone/blob/main/User_Page.png)

## Main Game Screen

### Shooting

- Each Tank and Snout are separate sprites that have been attached together using their relative positions and the angle of their current slope. This is helpful is aiming the snout for shooting.
- Each weapon is dynamically loaded using Template Design Pattern, reducing the LOC significantly, OOPs does make stuff easier. 🙈
- Health of the tank hit is reduced depending upon the distance of the impact of the weapon.

# Load Game Screen

- Games can be saved and loaded from the Load option present in the Main Menu
- Games are stored using the concept of Serialisation using `ObjectOutputStream`.
- All game details of an ongoing game are stored in a class called Play.

```java
try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("obj1.txt"))) {
oos.writeObject(play);
} catch (IOException e) {
e.printStackTrace();
}
```

- The class Play is serialised and the next slot index is stored using `BufferedWriter`.

```java
FileWriter fileWriter = new FileWriter(file);
BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);                    

bufferedWriter.write(towrite);
bufferedWriter.flush();
bufferedWriter.close();
```

- Finally, games are Loading using `ObjectInputStream`

```java
try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("obj1.txt"))) {
    Play deserializedObj = (Play) ois.readObject();
    game.setScreen(new MainGameScreen(game, deserializedObj));
} catch (IOException | ClassNotFoundException e) {
    e.printStackTrace();
}
```

![Saved_Game.png](https://github.com/UtsvGrg/TankStars-GameClone/blob/main/Saved_Game(Serialization).png)

## Exception Handling

- We have handled two exceptions, to ensure that the health of a player does not drop below zero and the terrain is not generated above half of the screen height.

## Use case Diagram

The following use case diagram shows the work flow of the game.

![Use Case Diagram - Tank Stars.png](https://github.com/UtsvGrg/TankStars-GameClone/blob/main/UML_Photo.png)
