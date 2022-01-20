# Starknet Boilerplate

A simple environment to start building on Starknet with Cairo. Uses Nile for compilation/deployment and Starknetjs for contract invokes/calls.

*Note: Mac and Mac M1 have special instructions at the bottom.*

# Setup

1. Install js dependencies
```npm install```

2. Install the latest Nile (equivalent to hardhat) with custom port availability
```
python3 -m venv env
source env/bin/activate
git clone https://github.com/OpenZeppelin/nile.git
env/bin/python3 -m pip install --upgrade pip
pip install ./nile
```

*Note: You'll run these commands every time you develop.*

3. Setup project
```nile init```

Optional: Add the following to your ~/.zprofile to quickly spin up your environment each time:
```alias envsetup="python3 -m venv env; source env/bin/activate; git clone https://github.com/OpenZeppelin/nile.git; env/bin/python3 -m pip install --upgrade pip; pip install ./nile; nile init"```

# Usage

Ensure you're in a Python environment (see step 2 above) before executing the following commands:

1. Spin up a node (in a separate terminal window w/ the python environment running)
```nile node --port localhost:5001```

*Note: Some systems have a conflict with port 5000 which is why I chose 5001*

1. Compiling and deploy a sample contract (in /contracts directory)
```npm run compile```

2. Run transactions against your contract
```npm run build```

These commands will test and deploy against your local node. If you want to deploy to the goerli testnet, use --network goerli instead.

# Starknet Setup on Mac M1

**Why do we need a special install guide?**
1. M1 Macs use a new architecture which is not compatible with some dependencies (e.g. homebrew). [More info](https://stackoverflow.com/questions/64963370/error-cannot-install-in-homebrew-on-arm-processor-in-intel-default-prefix-usr)*


1. Install Homebrew
```
/usr/sbin/softwareupdate --install-rosetta --agree-to-license
arch -x86_64 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
*Note: From here on out, you need to use `arch -x86_64 brew install <package>` to install packages w/ homebrew.*

2. Install required dependencies
```
arch -x86_64 brew install gmp
npm install
```

3. Install the latest Nile (equivalent to hardhat) with custom port availability
```
python3 -m venv env
source env/bin/activate
git clone https://github.com/OpenZeppelin/nile.git
env/bin/python3 -m pip install --upgrade pip
pip install ./nile
```

Optional: Add the following to your ~/.zprofile to quickly spin up your environment each time:
```alias envsetup="python3 -m venv env; source env/bin/activate; git clone https://github.com/OpenZeppelin/nile.git; env/bin/python3 -m pip install --upgrade pip; pip install ./nile; nile init"```