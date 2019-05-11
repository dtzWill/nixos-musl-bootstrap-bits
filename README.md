# NixOS Bootstrap w/musl - Bus Factor Mitigation

It's unlikely that the contents of this repository
are useful for you unless you use Nix and build
software based on Nixpkgs's musl support.

And even then, these are just copies of files you
likely already have locally anyway :).

## What

Copies of the the files used to "bootstrap" builds
in NixOS/Nixpkgs for musl-based configurations.

These should only be used after checking the hashes
(see Nixpkgs bootstrap expressions) and even then
the actual compilers used are checked to have no
references to any path derived from these tools.

The official locations are still on https://wdtz.org
at least for now.

## Why?

Partially for transparency but the main reason is I'd
feel better knowing they're available even if
I was [hit by a bus](https://en.wikipedia.org/wiki/Bus_factor).

All paths can be obtained from the ALLVM cache
or cachix, and a few are on https://cache.nixos.org
since they were built by the official hydra.

## This is not a nix store, these are incomplete

Nixpkgs' bootstrap artifact creation process
has the quirk that the compressed end result
is stored in the same path of the "nix store".
This means in order to access the small-ish
final artifacts, their much larger uncompressed
contents are always brought along and must
be stored as part of storing the paths.

This isn't a big problem--especially for a server
that otherwise has cause to have these files
in storage anyway-- but it means the most
natural way of archiving these (copies of the paths)
would be rather unreasonable for stashing on git.

Instead, these are only the portions of the paths
in the `on-server` directories--
basically, the "good stuff" used for bootstrapping.

It's **possible** that unpacking the tarball
would actually be perfect enough for the path
to be valid (hash-equivalent) but I haven't
tried it...yet.

