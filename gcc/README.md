# gcc

C and C++ compilers (`gcc` and `gcc-c++`) for the host.

For most development work, use a container (toolbox, distrobox, etc.) instead,
since building software usually also needs headers and `-devel` packages that
are not available on an image-based host.

This sysext is for tools that run directly on the host, need a compiler, and do
not work well from inside a container. For example:

- [Homebrew](https://brew.sh) needs a host compiler to build formulae from
  source and for some of its own setup.
- [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
  compiles parsers with the compiler available to Neovim. With a host Neovim
  (for example from the `neovim` sysext), this happens on the host, both for
  explicit installs and updates and, in many configs, automatically the first
  time a new file type is opened.

## Compatibility

This sysext is compatible with all Fedora variants (CoreOS, Atomic
Desktops, etc.).
