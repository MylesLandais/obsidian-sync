__DO NOT__ install nim from the Arch Community Repository

Use [ChooseNim](https://github.com/dom96/choosenim) 
```
export DO_NOT_TRACK=1
```
After disabling telemtry
```
curl https://nim-lang.org/choosenim/init.sh -sSf | sh
```
Add to .zshrc
```
export PATH=/home/alexei/.nimble/bin:$PATH
```