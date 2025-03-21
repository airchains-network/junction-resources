# 🚀 Junction v0.3.1 - Varanasi Testnet | Genesis Validator Guide  

Welcome to the **Junction v0.3.1 Varanasi Testnet!** This guide outlines the steps for validators to join the network from **genesis** by generating and submitting a **gentx (genesis transaction).**  

📅 **Submission Deadline:** **12:00 PM (Noon) GMT, March 19, 2025**  
🌐 **Official Repository:** [Junction v0.3.1](https://github.com/airchains-network/junction/tree/v0.3.1)  

---

## 🚀 Prerequisites  

Ensure you have the following before proceeding:  

- **Software:** Install the `junctiond` binary for v0.3.1. Download it from [GitHub Releases](https://github.com/airchains-network/junction/releases).  
- **Environment:** A Linux machine with **Golang, Rust, build-essential, jq, and basic CLI tools** installed..
- **Build-Essential and jq Installation:**  

  ```bash
  sudo apt update && sudo apt install -y build-essential jq
  ```

- **Go Installation (v1.22+):**  

  ```bash
  wget https://go.dev/dl/go1.22.2.linux-amd64.tar.gz  
  sudo tar -C /usr/local -xzf go1.22.2.linux-amd64.tar.gz  
  echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc  
  source ~/.bashrc  
  go version  # Verify installation  
  ```

- **Rust Installation (v1.80+):**  

  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh 
  rustc --version  # Verify installation  
  ```  

  Choose the default installation (option 1) when prompted

---

## ⚙️ Step-by-Step Instructions  

### 1️⃣ Install & Initialize the Node  

```bash
wget https://github.com/airchains-network/junction/releases/download/v0.3.1/junctiond-linux-amd64  
chmod +x junctiond-linux-amd64  
mv junctiond-linux-amd64 /usr/local/bin/junctiond  
junctiond init <your-moniker> --chain-id varanasi-1 --default-denom uamf
```

🔹 Replace `<your-moniker>` with your validator name.  

---

### 2️⃣ Create a Keypair  

```bash
junctiond keys add <key-name> --keyring-backend os  
```

🔹 Replace `<key-name>` with a unique name (e.g., `validator1`).  
🔹 Save your **mnemonic phrase** securely.  

---

### 3️⃣ Generate the gentx  

```bash
junctiond genesis add-genesis-account <key-name> 100000000000uamf  
junctiond genesis gentx <key-name> 100000000000uamf \  
  --chain-id varanasi-1 \  
  --moniker "<your-moniker>" \  
  --commission-rate "0.10" \  
  --commission-max-rate "0.20" \  
  --commission-max-change-rate "0.01" \  
  --min-self-delegation "1" \  
  --pubkey "$(junctiond tendermint show-validator)" \  
  --keyring-backend os  
```

🔹 Replace `<key-name>` with your key.  
🔹 Adjust **commission rates** as needed.  

---

### 4️⃣ Submit Your gentx  

#### 🔹 Fork & Clone the Repository  

```bash
git clone https://github.com/airchains-network/junction-resources.git  
cd junction-resources  
```

#### 🔹 Copy & Push gentx  

```bash
cp ~/.junctiond/config/gentx/gentx-<node-id>.json varanasi-testnet/gentxs/  
git add varanasi-testnet/gentxs/gentx-<node-id>.json  
git commit -m "Add gentx for <your-moniker>"  
git push origin main  
```

#### 🔹 Create a Pull Request (PR)  

Go to GitHub and submit a PR titled:  
`gentx: <your-moniker>`  

---

## ⏳ 5️⃣ Await Genesis Finalization  

- After **March 19, 2025 (12:00 PM GMT)**, the Airchains team will:  
  ✅ Aggregate the **gentx** submissions.  
  ✅ Publish the final **genesis.json** file.  
  ✅ Delegate tokens to ensure validators stay in the **active set**.  

---

Let's build together! 🚀  
