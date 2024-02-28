# Remote Cargo
Run cargo commands on a remote machine. The idea is loosely based on https://github.com/sgeisler/cargo-remote, but this repo provides significantly more functionality and is entirely based on bash scripts, so it is more portable/modifiable.

## Usage
The in-built help commands document `rcargo`:
```bash
rcargo

  Usage:
    rcargo <FLAG>
    rcargo <COMMAND> <SUBCOMMAND> [CARGO FLAGS]
  
  rcargo is a remote build tool for faster Rust development, using the Cargo
  package manager.

  Flags:
    -h, --help    show help message and exit

  Commands:
    help          show help message and exit

    build         Compile the current package
    check         Analyze the current package and report errors, but don't build object files
    clean         Remove artifacts that cargo has generated in the past
    run           Run a binary or example of the local package
    session       Manage multiple development sessions i.e. git branches
    sync          Sync local repository to remote, or vice versa
    test          Execute all unit and integration tests and build examples of a local package

  Try rcargo <COMMAND> -h (or --help) to learn more about each command.
  Default config is located at /usr/local/rcargo-cli/.rcargo/config
```

### Configuration
Check the `template_config` directory for sample configuration files. After installation, the default config file exists at `/usr/local/rcargo-cli/.rcargo/config`. This config can be overridden if you place a `.rcargo/config` in the directory from which you are running `rcargo` commands.

## Install
If your project's template config is not already in the `template_config` directory, please create one first. Following is a sample installation for the gear project.
```bash
git clone https://github.com/kapilsinha/rcargo-cli && ./rcargo-cli/install ./rcargo-cli/template_config/gear_ukint.template

Enter the path to your project directory (defaults to '/placeholder/path/to/local_dir')
This is your local mirror to the remote's /home/kapil/Desktop/gear
/Users/kapil/Desktop/gear

Git session manager automatically changes your remote workspace's 'session' based on your local git branch. 
This can help if you tend to concurrently develop on multiple branches.
Enable git session manager? (Y/n)  y

Auto-sync will rsync your local files to the remote machine before every cargo command. 
NOTE: Only use this if you do not use remote development, or you will lose your remote changes!
Enable auto-sync? (Y/n)  y

Installing rcargo to /usr/local/bin ...
building file list ... done
rcargo-cli/
rcargo-cli/.rcargo/config
<Remaining list of files>
sent 8273 bytes  received 252 bytes  17050.00 bytes/sec
total size is 7517  speedup is 0.88

Config (/usr/local/rcargo-cli/.rcargo/config):
<Config printed to stdout>
```
