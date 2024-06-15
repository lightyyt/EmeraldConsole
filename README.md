# EmeraldConsole
A Easy-To-Use Godot Developer Console with high customizability

## How to Use
1. Download EmeraldConsole from the Godot AssetLib
2. Add the EmeraldConsole Node to All of your Scenes
3. Add Custom Commands easily!

## How to add Commands
1. Create a new GDScript file and add it to any Node (except the EmeraldConsole you added)
2. In the _ready() function add: `EmeraldConsole.add_command("Command Name", "Command Description", ["argument1", "argument2", "..."], command_function)`
3. Add your command function.
   - If you have arguments, like this: `func command_function(args):`
   - If you dont have arguments, like this: `func command_function():`
4. Code your Command
5. (Optional) Add EmeraldConsole logging
   - Log: `EmeraldConsole.send_log("string")`
   - Warning: `EmeraldConsole.send_warn("string")`
   - Error: `EmeraldConsole.send_error("string")`
 6. Use Your Command!

### Sample Script:
```
extends Control
func _ready():
  # Register Commands
  EmeraldConsole.add_command("test", "Testing Command", [], command_test)
  EmeraldConsole.add_command("hello", "Prints Hello + arg", ["text"], command_hello)
  EmeraldConsole.add_command("random_cmd", "Runs either version or help", [], command_random)

#Command Functions
func command_test():
  EmeraldConsole.send_log("This is a Log Message")
  EmeraldConsole.send_warn("This is a Warning Message")
  EmeraldConsole.send_error("This is an Error Message")

func hello(args):
  # The aruments can technically be as many as the user specifies, but they will be split by spaces!
  EmeraldConsole.send_log("Hello, "+args[0])

func random_cmd():
  if randi_range(0, 1) == 0:
    EmeraldConsole.run_string_as_command("help")
  else:
    EmeraldConsole.run_string_as_command("version")
```
