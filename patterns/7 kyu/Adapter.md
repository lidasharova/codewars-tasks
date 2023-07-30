## Description:

The Adapter Design Pattern can be used, for example in the StarCraft game, to insert an external character in the game.

The pattern consists in having a wrapper class that will adapt the code from the external source.

### Task

The adapter receives an instance of the object that it is going to adapt and handles it in a way that works with our application.

In this example we have the pre-loaded classes:

```
class Marine {
  attack(target) {
    target.health -= 6;
  }
}

class Zealot {
  attack(target) {
    target.health -= 8;
  }
}

class Zergling {
  attack(target) {
    target.health -= 5;
  }
}

class Mario {
  jumpAttack() {
    console.log('Mamamia!');
    return 3;
  }
}

```

Complete the code so that we can create a MarioAdapter that can attack as other units do.

Note to calculate how much damage mario is going to do you have to call the jumpAttack method.

## Solution:

```javascript
class Probe {
  constructor() {
    this.commands = [];
    this.position = { x: 0, y: 0 };
    this.minerals = 0;
  }

  move(x, y) {
    const moveCommand = new MoveCommand(this, x, y);
    this.commands.push(moveCommand);
  }

  gather() {
    const gatherCommand = new GatherCommand(this);
    this.commands.push(gatherCommand);
  }
}

class MoveCommand {
  constructor(unit, x, y) {
    this.unit = unit;
    this.x = x;
    this.y = y;
  }

  execute() {
    this.unit.position.x = this.x;
    this.unit.position.y = this.y;
  }

  canExecute() {
    return true;
  }
}

class GatherCommand {
  constructor(unit) {
    this.unit = unit;
  }

  execute() {
    if (this.unit.minerals === 0) {
      this.unit.minerals += 5;
    }
  }

  canExecute() {
    return this.unit.minerals === 0;
  }
}
```
