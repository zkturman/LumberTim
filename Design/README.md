# Overall Design Specification #

This mobile game features a lumberjack named Tim who cuts downs trees. Players will guide Tim as he progresses through his career as a lumberjack by helping him chop down trees. Users will collect currency for cutting down trees and as their skills progress, they will be able to cut down more difficult trees.

## [Home Scene](DesignSpecifications/HomeSceneSpec.md) ##
On the home scene, users must be able to take three different actions and do the following
* Select an action for playing the game that opens the Gameplay Base Scene
* Select an option to configure settings that opens a new scene
* Close the application (although this will be a native functionality for a mobile device)
* Log seconds played to file
* Displays tooltip if first time playing (logs this to persistent storage after being dismissed)

## Gameplay Base Scene ##

The gameplay base scene serves as a hub for player actions when playing the game. Here the player will be able to do the following
* Open a list of trees to cut (modal window)
  * See all possible trees to cut, with locked trees appearing in silhouette 
  * Select a tree to cut and open the Tree Chopping Scene (possible modal window)
    * If a current tree is in progress, asks if you would like to abandon tree. Yes goes to Tree Chopping scene with new tree. This erases the previous tree's progress
    * No returns tree selection
    * Continue goes to existing tree
  * Unlock a new tree from the list (model window)
    * Confirm unlocking the tree (closes modal)
    * Deny unlocking the tree (closes modal)
  * Scroll through the list of trees
  * Continue previous tree  and open the Tree Chopping Scene, loads information from file
  * Close the modal window
* Open the game store (modal window)
  * See all possible perks, with locked perks appearing in silhouette
  * See player currency
  * Tap a perk to purchase (modal window)
    * Confirm perk purchase (closes modal)
    * Deny perk purchase (closes modal)
  * Scroll through perks
  * Close modal window
* See player stats and perks (modal window)
  * See all player stats
  * Scroll if information exceeds window
  * Remove perk (modal window)
    * Displays currency to return (half of purchase cost)
    * Confirm removal (closes modal)
    * Deny removal (closes modal)
  * See player avatar
  * Click player avatar to edit (opens modal)
    * Change flannel colour by scrolling options
    * Change beard colour by scrolling options
    * Change axe sprite by scrolling options
    * Store avatar information to file
* See player currency
* See player avatar, load information from file
* Log seconds played to file, if maximum exceeded goes to Rest Scene
* Shows mini tutorial tooltips in order of tree selection, store, and player stats. The next tooltip displays when the previous one is dismissed. When dismissed, this is stored persistently
* Return to the Home scene

## Tree Chopping Scene ##

In this scene, players work to chop down a singular tree. A tree can take a variable range of chops to fell, and this range scales with the difficulty of the tree. In this scene, users can do the following
* Tap an area of the screen to chop the tree (an animation plays for this)
* See the lumberjack chop the tree
* See the tree's progress towards felling (different sprites for different percentages of progress)
* When the tree will fall down and the level will complete (modal window)
  * Displays the tree's reward
  * Allows players to return to the Gameplay Base Scene
* Players can return to the Gameplay Base Scene
* Players can exit the game
* Any auto-chopping is calculated when opening the tree and a message is displayed to players
* Logs seconds played to file
* Small banner advertisements are displayed
* Tutorial tooltips display upon the first play and are dismissed when the player starts chopping the tree
* Logs the number of total chops to persistent storage.

## Settings Scene ##

Players can configure persistent settings for the game.  Players can do the following in this scene
* Define what time is considered the start of a new day (e.g. 0800 vs 0900).
* Define game volume (sound effects and music)
* Define brightness
* Define how long they can play the game each day (e.g. from 15 to 60 min); there is a system defined maximum
* Delete all game data (modal window)
  * Players can confirm they want to delete their data (modal window)
    * Players can confirm once again they want to delete
    * Players can decline and go back to the Settings Scene
  * Players can decline and go back to the Settings Scene
* Remove ads for 0.50p (modal window)
  * Players can confirm they want to go ad free
  * Players can decline and return to settings

## Rest Scene ##

This scene is the default scene if players exceed the max amount of time allowed per day. The following happens on this page
* An animation plays with the lumberjack
* A countdown until the next day when you can play again displays (note, this is configurable in settings. By default it is 0700)
* If the countdown reaches 0 while open, then it will reload the Home Scene
* Players see a message that provides a fact about screen time on their phones
