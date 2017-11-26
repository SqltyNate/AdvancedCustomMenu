# Click Handlers #
***
```yaml
Click-Handlers:
  <UNIQUE-ID>:
    Click-Type: 'left, right, middle'
    Shift: false
    Commands:
    - 'me I am awesome!'
    Price: 10
    Price-Message: '%prefix% &7Seems like you are not rich enough to be awesome, you must have $%price%!'
    Points: 100
    Points-Message: '%prefix% &7Seems like you don''t have %points% points to use this!'
    Experience: 10L
    Experience-Message: '%prefix% &cWhoops! &7Seems like you are not ''experienced'' enough ;) You must have atleast %experience% experience!'
    Permission: 'example.savage'
    Permission-Message: '%prefix% &cLooks like you are not savage enough to use this command!'
    Close: true
    Delay: 10
    Delay-Message:
    - '%prefix% Too fast! You must wait {secondsleft} secs to use this again!'
    Sounds:
      Basic: 'ITEM_ARMOR_EQUIP_GENERIC'
      Success: 'ITEM_TOTEM_USE'
      Failed: 'ENTITY_GHAST_DEATH'
```
### Summary ###
- [Click-Type](#click-type)
- [Shift](#shift)
- [Price](#price)
- [Price-Message](#price-message)
- [Points](#points)
- [Points-Message](#points-message)
- [Permission](#permission)
- [Permission-Message](#permission-message)
- [Experience](#permission)
- [Experience-Message](#permission-message)
- [Commands](#commands)
- [Close](#close)
- [Delay](#delay)
- [Delay-Message](#delay-message)
- [Sounds](#sounds)
***
- #### Click-Type ####
***
  Info: The click type a player must click an item to allow execution  
  Execution: Upon a player clicks the item  
  Default Value: none  
  Value Type: String Array  
  ~~------~~  
  The available nodes are listed below
  These can all be combined using commas *(ex: 'left, right, middle')*
  - **left** player must left click
  - **right** player must right click
  - **middle** player must middle click
  
***
- #### Shift ####
***
  Info: Specifies whether the handler needs a shift click  
  Execution: After [Click-Type](#user-content-click-type) if passed successfully   
  Default Value: none  
  Value Type: String  
  ~~------~~  
  The available nodes are listed below
  - **true** player must click the item while shifting
  - **false** player must click the item without shifting
***
- #### Price ####
***
  Info: The amount of Vault money required for the handler to execute commands  
  Execution: After [Delay](#delay) if passed successfully  
  Extra: [Vault](https://www.spigotmc.org/resources/vault.41918/) and an economy plugin like [Essentials](https://hub.spigotmc.org/jenkins/job/spigot-essentials/) needed to be enabled!  
  Value Type: Integer  
***
- #### Price-Message ####
***
  Info: The message to send when the player does not have enough [Price](#price)  
  Default Value: [config message](#config.md)  
  Value Type: String List  
  Example:
  ```yaml
  Price: 100
  Price-Message:
  - '&cSorry %player_name%! &7You must have atleast $%price% to buy this!'
  ```
  Extra:  
   - Supports [placeholders](#api/placeholders.md)  
   - **%price%** Display the price of the click-handler  
***
- #### Points ####
*Added in 2.1.2*
***
  Info: The amount of points required for the handler to execute commands  
  Execution: After [Delay](#delay) if passed successfully  
  Extra: [PlayerPoints](https://dev.bukkit.org/projects/playerpoints) need to be enabled!  
  Value Type: Integer  
***
- #### Points-Message ####
***
  Info: The message to send when the player does not have enough [Points](#points)  
  Default Value: [config message](#config.md)  
  Value Type: String List  
  Example:
  ```yaml
  Points: 25
  Price-Message:
  - '&cSorry %player_name%! &7You must have atleast $%points% to buy this!'
  ```
  Extra:  
   - Supports [placeholders](#api/placeholders.md)  
   - **%points%** Display the points of the click-handler  
***
- #### Experience ####
*Added in 2.2.0*
***
  Info: The amount of experience points required for the handler to execute commands  
  Execution: After [Delay](#delay) if passed successfully  
  Extra: It can be an integer like "17" or "4", but you can add an "L" *(ex:"10L")* for levels!  
  Value Type: Float  
***
- #### Experience-Message ####
***
  Info: The message to send when the player does not have enough [Experience](#experience)  
  Default Value: [config message](#config.md)  
  Value Type: String List  
  Example:
  ```yaml
  Experience: 10L #Takes 10 Levels, and not 10 Exp points
  Experience-Message:
  - '&cSorry %player_name%! &7You must have atleast %experience% Exp to buy this!'
  ```
  Extra:  
   - Supports [placeholders](#api/placeholders.md)  
   - **%experience%** Display the points of the click-handler  
***
- #### Permission ####
***
  Info: The permission required to use this click handler  
  Execution: After [Price](#user-content-price)
  Extra: Use a '-' to not require the permission
  Value Type: String
***
- #### Permission-Message ####
***
  Info: The message to send when the player does not have [Permission](#user-content-permission)  
  Default value: Default "NoPermission" message  
  Extra: Supports [placeholders](#api/placeholders.md)  
  Value Type: String List  
  ~~------~~  
  Example:
  ```yaml
  Permission: 'donator.epic'
  Permission-Message:
  - '&cSorry %player_name%! &7You must be an &eEpic&7 donator to do this!'
  ```
***  
- #### Commands ####
***
  Info: List of commands to execute once a click-handler passed succesfully  
  Execution: If the player has passed all the above click handlers  
  Extra: Supports [placeholders](#api/placeholders.md)   
  Value Type: List Strings  
  ~~------~~  
  You can start off a command with any of the following to execute a special event to a player
  - **menu: \<menu name without '.yml'\>** Open another menu without using "/acm open \<menu\>"
  - **server: \<server\>** Connect a player to a specific bungeecord server
  - **player: \<command\>** Execute the command as the player *(Default)*
  - **console: \<command\>** Execute the command as console
  - **chat: \<message\>** Make the player send a chat message
  - **message: \<message\>** Send a chat message to the player
  - **broadcast: \<message\>** Send a message to every player online
  - **give: \<item\>** Give a player an item *(same syntax as a frames [item](frames.md#item---required))*
  - **op: \<command\>** Execute a command as an operator
  - **tellraw: \<json message\>** Send a [json](https://www.minecraftjson.com) message to the player
  - **tellallraw: \<json message\>** Send a json message to *ALL* online players
  - **banner: \<banner-pattern\>** Give a banner with the specified [pattern](frames.md#banner-pattern)
***
- #### Close ####
***
  Info: Closes the menu after a click handler  
  Default Value: 'false'  
  Value Type: String  
  ~~------~~  
  Available nodes are listed below
  - **true** will close the menu after the player clicks
  - **false** will not close the menu
  - **onsuccess** will close if all click-handlers were successfully passed
***
- #### Delay ####
***
  Info: Delay in seconds that a player must wait to click an item again  
  Default Value: null  
  Value Type: Integer
***
- #### Delay-Message ####
***
  Info: The message to send to a player when a delay is active  
  Default Value: null  
  Value Type: String List  
  ~~----------~~  
  Special Placeholders:  
  - **{hoursleft}**: get the amount of hours left
  - **{minutesleft}**: get the amount of minutes left in the hour
  - **{secondsleft}** get the amount of seconds left in the minute
***
- #### Sounds ####
*Added in 1.4.0*
***
  Extra: More sounds can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)!  
  Info: The sounds to send to a player under a specific circumstance  
  Format: \[Sound\]:\<volume\>:\<pitch\>  
  Extra: Volume and Pitch can be a double (Ex: '0.3' or '0.7')  
  Value Type: Key List  
  ~~----------~~  
  Types:  
  - **Basic**: Executed everytime the item is clicked
  - **Success**: Played if the click-handlers were successful
  - **Failed**: Played if the click-handlers did not pass
