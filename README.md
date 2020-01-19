# Sharingan

<p align="center">
	<img src="./icon.jpg" width="35%" >
</p>

Sharingan is a recon multitool for offensive security / bug bounty

This is very much a work in progress and I'm relatively new to offensive security in general so if you see something that can be improved please open an issue or PR with suggested changes.

## Cloning for development
Outside of your gopath
`git clone https://github.com/leobeosab/sharingan`

## Installing
`go get github.com/leobeosab/sharingan/cmd/sharingancli`

## Dependencies
*   NMap
*   Go

## Usage
#### Note
Order matters when it comes to flags it must be `sharingancli [globalflags] command [commandflags]` if this isn't a wanted feature I can change it but I like how clean it is

### DNS
#### bruteforce
DNS busts the target with a wordlist you provide 
```
sharingancli --target targetname dns --dns-wordlist ~/path/to/wordlist --root-domain target.com
```
![dns example gif](./dns_example.gif)

#### addsubs
Adds subdomains to the program's storage from stdin using pipes
```
cat subs | sharingancli --target targetname dns addsubs
```

### Scan
Scans all hosts available that were stored in target using nmap
```
sharingancli --target target scan
```
![scan_example_gif](./scan_example.gif)

#### interactive
Scan a single host from list of subdomains stored in target 
```
sharingancli --target target scan interactive
```
![scan interactive_example gif](./scan_interactive_example.gif)

### info
#### domains
Outputs all domains as a list in stdout
```
sharingancli --target target info domains
```
![info example](./info_example.png)

## TODO in shor term
*   Nmap interactive port storage
*   add a way to do SYN / -sS scanning [ must be root so it presents a challenge ]

## Roadmap? 
*   Better progress bars
*   JSON and regular file exports
*   Automated scans through a daemon?
*   Dir brute forcing
*   Possible Web ui / html export
