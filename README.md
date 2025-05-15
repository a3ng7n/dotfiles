# what

bootstrap

```bash
# shell
sudo apt install zsh
chsh -s $(which zsh)
git clone https://github.com/jeffreytse/zsh-vi-mode.git $HOME/.zsh-vi-mode

# install chezmoi
wget https://github.com/twpayne/chezmoi/releases/download/v2.59.1/chezmoi_2.59.1_linux_amd64.deb
sudo dpkg -i chezmoi_2.59.1_linux_amd64.deb
rm chezmoi_2.59.1_linux_amd64.deb

# get dotfiles
chezmoi init https://github.com/a3ng7n/dotfiles.git
chezmoi diff
chezmoi apply -v

# misc
sudo apt install curl gnupg2

# fonts
mkdir -p ~/.fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/FiraCode.zip
unzip FiraCode.zip -d ~/.fonts
fc-cache -fv

# term
curl -L https://sw.kovidgoyal.net/kitty/installer.sh | sh /dev/stdin

# Add kitty to the ubuntu desktop ecosystem :/
mkdir -P ~/.local/bin
ln -sf ~/.local/kitty.app/bin/kitty ~/.local/kitty.app/bin/kitten ~/.local/bin/
cp ~/.local/kitty.app/share/applications/kitty.desktop ~/.local/share/applications/
cp ~/.local/kitty.app/share/applications/kitty-open.desktop ~/.local/share/applications/
sed -i "s|Icon=kitty|Icon=$(readlink -f ~)/.local/kitty.app/share/icons/hicolor/256x256/apps/kitty.png|g" ~/.local/share/applications/kitty*.desktop
sed -i "s|Exec=kitty|Exec=$(readlink -f ~)/.local/kitty.app/bin/kitty|g" ~/.local/share/applications/kitty*.desktop
echo 'kitty.desktop' > ~/.config/xdg-terminals.list

# Set kitty as default terminal
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator $(which kitty) 50

# python dev
sudo apt install python3.12-venv

# install uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# neovim
sudo apt install make gcc ripgrep unzip git xclip fd-find luarocks
sudo add-apt-repository ppa:neovim-ppa/unstable
sudo apt update
sudo apt install neovim

# fzf
sudo apt install fzf

# lazygit
LAZYGIT_VERSION=$(curl -s "https://api.github.com/repos/jesseduffield/lazygit/releases/latest" | grep -Po '"tag_name": "v\K[^"]*')
curl -Lo lazygit.tar.gz "https://github.com/jesseduffield/lazygit/releases/latest/download/lazygit_${LAZYGIT_VERSION}_Linux_x86_64.tar.gz"
tar xf lazygit.tar.gz lazygit
sudo install lazygit /usr/local/bin
rm lazygit
rm lazygit.tar.gz

# install littany of c build tools
sudo apt install g++ autoconf libtool

# install node bs
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# reload terminal...
nvm install 19.6.1

# install google cloud client
sudo apt-get install apt-transport-https ca-certificates gnupg curl
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
sudo apt-get update && sudo apt-get install google-cloud-cli
# run `gcloud init` to get started
```
