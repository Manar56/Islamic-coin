## Haqq Node Setup

# hardware requirements:

CPU	4 RAM  8GB	Storage 100GB

# Before Installation

```sudo apt update && sudo apt upgrade -y```

```sudo apt install curl tar wget clang pkg-config libssl-dev libleveldb-dev jq build-essential bsdmainutils git make ncdu htop screen unzip bc fail2ban htop -y```

#  GO Installing

```ver="1.18.3" && \
cd $HOME && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile```

# Binary Installing

```cd $HOME
git clone -b v1.0.3 https://github.com/haqq-network/haqq 
cd haqq
make install```

# Moniker 

```haqqd init $HAQQNODE --chain-id $HAQQCHAIN```

# Add wallet

```haqqd keys add <walletName>```

# Recovery Old wallet
```haqqd keys add <walletName> --recover```

# Genesis Update

```haqqd tendermint unsafe-reset-all --home $HOME/.haqqd
rm $HOME/.haqqd/config/genesis.json
wget -O $HOME/.haqqd/config/genesis.json "https://storage.googleapis.com/haqq-testedge-snapshots/genesis.json"
wget -O $HOME/.haqqd/config/addrbook.json "https://raw.githubusercontent.com/StakeTake/guidecosmos/main/haqq/haqq_53211-1/addrbook.json"```

# Seeds

```SEEDS="8f7b0add0523ec3648cb48bc12ac35357b1a73ae@195.201.123.87:26656,899eb370da6930cf0bfe01478c82548bb7c71460@34.90.233.163:26656,f2a78c20d5bb567dd05d525b76324a45b5b7aa28@34.90.227.10:26656,4705cf12fb56d7f9eb7144937c9f1b1d8c7b6a4a@34.91.195.139:26656"
PEERS="22a64e0d99ceb809fb902c4b1f91918553b06e9b@173.249.38.80:36656,0e8de1037b15af79705174d43c5fee1a93ac92ca@116.203.35.46:36656,583b6585d34e9993a7b02a8faa057d6334de30e6@65.109.17.86:31656,ffadba4c95ad235c828763e35cddee3fd2a35892@78.107.234.44:45666,d09e4b49d27a4d0a8a338157afb9674af0bb0da3@65.109.30.117:27656,9f15d378fda449c030eea4f913c1fee26a3046f5@65.109.18.179:33656,1ab6eba1e24b195a51a5a8e960f6328a4782b43c@195.201.108.152:26656,c3ee2e7ad7533d589e6de8b7cb146495a88a744c@135.181.248.69:46656,952b9d918037bc8f6d52756c111d0a30a456b3fe@213.239.217.52:29656"; \
sed -i.bak -e "s/^seeds *=.*/seeds = \"$SEEDS\"/; s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" $HOME/.haqqd/config/config.toml```










