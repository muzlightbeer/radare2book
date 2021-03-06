# Configuration

The core reads ~/.radare2rc while starting, so you can setup there some `e` commands to set it up in your favorite way.

To avoid parsing this file, use `-n` and to get a cleaner output for using radare in batch mode maybe is better to just drop the verbosity with `-v`.

All the configuration of radare is done with the `eval` command which allows the user to change some variables from an internal hashtable containing string pairs.

The most common configuration looks like this:

    $ cat ~/.radarerc
    e scr.color = true
    e dbg.bep   = loader
    
    
These configurations can be also defined using the `-e` flag of radare while loading it, so you can setup different initial configurations from the commandline without having to change to rc file.

    $ radare -n -e scr.color=true -e asm.syntax=intel -d /bin/ls
    
All the configuration is stored in a hash table grouped by different root names (cfg., file., dbg., ..)

To get a list of the configuration variables just type `e` in the prompt. All the basic commands can be reduced to a single char. You can also list the configuration variables of a single eval configruation group ending the command argument with a dot `.`.

There are two enhanced interfaces to help users to interactively configure this hashtable. One is called `emenu` and provides a shell for walking through the tree and change variables.

To get a help about this command you can type `e?`:

    Usage: e[?] [var[=value]]
    e?              show this help
    e?asm.bytes     show description
    e??             list config vars with description
    e               list config vars
    e-              reset config vars
    e*              dump config vars in r commands
    e!a             invert the boolean value of 'a' var
    er [key]        set config key as readonly. no way back
    ec [k] [color]  set color for given key (prompt, offset, ...)
    e a             get value of var 'a'
    e a=b           set var 'a' the 'b' value
    env [k[=v]]     get/set environment variable

       
There is a easier `e` interface accessible from the Visual mode, just typing `Ve` after entering this mode.

    Eval spaces:                                                                   
    
    >  anal                                                                        
       asm                                                                         
       scr                                                                         
       asm                                                                         
       bin                                                                         
       cfg                                                                         
       diff                                                                        
       dir                                                                         
       dbg                                                                         
       cmd                                                                         
       fs                                                                          
       hex                                                                         
       http                                                                        
       graph                                                                       
       hud                                                                         
       scr                                                                         
       search                                                                      
       io                                                                          
   


Most of the eval tree is quite stable, so don't expect hard changes on this area.

I encourage you to experiment a bit on this to fit the interface to your needs.
