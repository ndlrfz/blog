+++
date = '2025-02-04T17:41:12+07:00'
draft = false
tags = ["neovim"]
title = 'Neovim Multiple Configs'
+++

## Intro

If you're Neovim fan, it is important to have multiple configs. You can configure like this:

* `~/.config/nvim`: Your main configuration. When you're working on your project, this is the configuration that will be loaded.
* `~/.config/nvim-alt`: Your secondary Neovim configuration where you can implement new things.

So now, let's configure it.

## Setup Neovim Playground

Assuming that your main Neovim configured, let's configure the alternate Neovim configuration.

This example wll be using *kickstart.nvim* as an alternative configuration. You can choose other starterkit like *Lazy.nvim* or distribution like *Nvchad*, *Astro*, etc.

```bash
git clone https://github.com/nvim-lua/kickstart.nvim.git "${XDG_CONFIG_HOME:-$HOME/.config}"/nvim-alt
```

Now you can start start Neovim with the `nvim-alt` configuration using the command below.

```bash
NVIM_APPNAME=nvim-alt nvim
```

## Adding Neovim Playground to bashrc/zshrc

The efficient to do this is to create an alias through `~/.bashrc` or `~/.zshrc` file:

```bash
echo "alias nvimalt='NVIM_APPNAME=nvim-alt nvim'" >> ~/.bashrc # or ~/.zshrc

# for Bash user
source ~/.bashrc

# for ZSH user
source ~/.zshrc
```

You can now run Neovim alternative with the `nvimalt` command.
