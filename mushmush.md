## Packing and Shipping with a conveyor belt and unconstructed boxes

Here's the agent's happy path:

1. A dedicated section of the conveyor belt arrives at their boxing station.
1. They advance the belt to for the new items that need to be packed.
1. They get* the right box and pack up the items.
1. They push boxed items back on the conveyor belt.
1. They check their box stock at their station.

### Breakdown of each use case above

A dedicated section of the conveyor belt arrives at their boxing station.

```java
packShipClock
refillBoxClock

ConveyorBelt {
  
  advanceBelt {
    startPackShipClock;
    return items;
  }
  
  reloadItemsOnConveyorBelt {
    return numberOfNewItems;
  }
}

ShipStation {
  refillBoxFlats {
    advanceRefillClock();
    return list(noOfSmBx,noOfMedBx,noOfLg);
  }
  
  packItems {
    getCorrectBox(hasBoxStock);
    buildBox(boxFlat);
    boxItems(items);
    return boxedItems;
  }
  
  pushItems {
    stopPackShipClock;
    return boxedItems;
  }
}

EffiBoard {
  numberMissed;
  numberBoxed;
  numberAdvanced;
  secondsOnShift;
  secondsOnBreak;
}

```

