# Shared Item Pickup

## Desc
Gives each currently alive player a copy of whatever item was just picked up (barring equipment).
Made so player greed does not result in other players becoming weak due to lack of items.
Chest spawnrate, teleporter rewards e.t.c were not changed.

Only host needs the mod.

## Installation
Replaces Assembly-CSharp.dll in:
\steamapps\common\Risk of Rain 2\Risk of Rain 2_Data\Managed\Assembly-CSharp.dll

**Backup current dll**

## Source/Do It Yourself
Edits Assembly-CSharp.dll -> RoR2 -> GenericPickupController -> GrantItem() -> line 214

Change:
inventory.GiveItem(this.pickupIndex.itemIndex, 1);

Into:
foreach (PlayerCharacterMasterController playerCharacterMasterController in PlayerCharacterMasterController.instances)
{
	if (playerCharacterMasterController.master.alive)
	{
		playerCharacterMasterController.master.GetBody().inventory.GiveItem(this.pickupIndex.itemIndex, 1);
	}
}

There's probably a few better ways of doing this, but It Just Works(TM)