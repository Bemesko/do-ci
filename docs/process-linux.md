# Linux Processes Cheatsheet
## Concepts
- Processes
	- mainfestation of a running program in a system
	- all process have an unique ID
	- are always spawned by a parent process, except by the ID 1
	- are closely tied to the user that created them
	- have an intrinsic priority
- Process State
	- Processes always have an associated state that indicates the stage in its execution
	- States consist of:
		- New
		- Ready
		- Running
		- Blocked
		- Suspended Ready/Blocked
		- Terminated
- Creating processes
	- On boot, the PID 1 is created, usually systemd
		- It runs all other processes on the system, so it's everyone's parent
	- When you run a command in the terminal, a new process is created
		- The process for the command you ran is the process for the terminal itself
- Foreground vs Background
	- Foreground processes can interact directly with the user, whereas background processes cannot
	- That being said, background processes can still send their output to stdout in a terminal
### Signals
- Used to externally change the state of a process, essentially
- Most commonly used to stop programs, from most gracious to most agressive:
	- 15 - SIGTERM
		- Ask nicely for the process to *terminate*
	- 19 - SIGSTOP + 18 - SIGCONT
		- *Stop* and resume (*continue*) a process' execution
		- Equivalent of using `Ctrl + Z` in a terminal
	- 2 - SIGINT
		- Ask a bit less nicely to *interrupt* a process
		- Equivalent of using `Ctrl + C` in a terminal
	- 1 - SIGHUP
		- Signals for the process to *hang up* its execution, no one wants it around anymore
		- Equivalent of closing the terminal with the process still running
	- 9 - SIGKILL
		- Just fucking *KILL* the process whether it wants to or not
## Commands
- `sleep` - useful when giving examples because it is very simple and runs for a long time
### Displaying processes
- `ps -faux` - Lists processes
	- `f` show processes in a tree-like syntax
	- `a` shows processes from all users
	- `u` displays which user the process belongs to
	- `x` lists processes even if they weren't started in the current terminal session
	- `pgrep`
- `jobs -l` - Lists background processes (jobs) of the current terminal session
	- `l` to also display the job's process Id
- `top` displays a cool view of all process in the system
	- `htop` displays a cooler view
### Interacting with processes
- `bg` and `fg` - move a process to the background/foreground, respectively
- `nohup` - make a process persist after the terminal is closed
	- stores the output in a nohup.out file
	- `nohup` - No Hang Up
- `exec` - quits the terminal session when the command exists
- `nice` and `renice` - Change priority of a process, `renice` is used for already created process
- `kill`
	- `pkill`
# References
https://www.youtube.com/watch?v=TJzltwv7jJs
https://www.youtube.com/watch?v=LfC6pv8VISk
https://www.geeksforgeeks.org/difference-between-process-and-thread/
https://www.geeksforgeeks.org/processes-in-linuxunix/
https://www.geeksforgeeks.org/process-management-in-linux/
https://www.geeksforgeeks.org/introduction-of-process-management/
https://www.cyberciti.biz/faq/unix-linux-jobs-command-examples-usage-syntax/
https://www.certificacaolinux.com.br/comando-linux-top/#:~:text=O%20Comando%20top%20no%20Linux,mais%20processos%20agem%20no%20sistema.
