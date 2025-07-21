# 📘 Netrum Light Node: Frequently Asked Questions (FAQ)

**1. Which network does the Netrum Light Node operate on Base Mainnet or Sepolia?**
- The Netrum Light Node operates on the Base Mainnet. All registrations, mining, and claims are on-chain, and all activity is verifiable on BaseScan. Sepolia is not used in this process.

**2. What fees are required to run the node?**
- To register your node on-chain, you’ll need a small amount of Base ETH to cover gas fees. Typically, the fee ranges between 0.0002–0.0005 Base ETH, but it may vary depending on network conditions.
- We recommend keeping at least $0.50–$1.00 worth of Base ETH in your wallet when starting.

**3. I received “Address not registered in database” when trying to mine. What should I do?**

 This usually happens if:

- You registered the node without being in the root directory, or
- The node registration was incomplete locally, even though it's completed on-chain.

Solution:

- Switch to the root user (`sudo su` or log in as root).
- Run the registration again:

```bash
netrum-node-register
```

> Don’t worry, the contract won't double-register your address. This will only re-sync your local config.

**4. My netrum-sync-log shows errors like “No such file or directory.” What’s wrong?**

This happens when the node tries to access files in the wrong path, typically because the setup was done in the wrong directory.

Fix it with these steps:

- Switch to your root directory:

```bash
cd ~
```

- Clone the repo from the root, not from subfolders:

```bash
git clone https://github.com/NetrumLabs/netrum-lite-node.git
```

- Then navigate into the folder:

```bash
cd netrum-lite-node
```

- Install dependencies:

```bash
npm install
npm link
```

> Avoid running setup in nested paths like `/home/user/folder/folder/netrum-lite-node.`

**5. I see sync errors even after setup. How do I reset or fix it?**

Try the following clean restart steps:

```bash
rm -rf /etc/systemd/system/netrum-node.service
netrum-sync
netrum-sync-log
```

- If the sync still fails, check system logs with:

```bash
sudo systemctl status netrum-node.service
```

- You can also manually trigger the sync script:

```bash
node /root/netrum-lite-node/src/system/sync/service.js
```

**6. How do I ensure I’m running the node from the correct directory?**

- Switch to root:

```bash
sudo su
```

- Clone the repo from the root directory.

```bash
ls
```

> and confirm you see the `netrum-lite-node` folder directly in `/root.`

```bash
npm install
netrum-system
netrum-sync
```

**7. I’m new to running nodes. Is there a browser-based version coming?**

- Yes! We’re working on a browser-based version of the node that will allow users to participate without VPS setup.
- It’s expected to be live publicly very soon.
- Until then, we recommend using a 6GB RAM, 2-core VPS with Ubuntu 22.04+ to run the CLI version.

**8. What is the reward system for running the node?**

- Once your node is synced and mining, you’ll earn NPT tokens daily based on your uptime. These are real, on-chain tokens streamed directly to your wallet every 24 hours.
- No points. No backend logic. All data is visible on BaseScan.

**9. Still stuck or confused?**

If you need help:

- Ask in the `🛠️┃node-operator` channel.
- Send screenshots of the errors and your directory structure.
- Tag team members or moderators for support.
