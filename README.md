# Monero Node

This Dockerfile provides a convenient way to run a Monero node using your own copy of the blockchain. It gives you complete control over your Monero node.

## Overview

Running a Monero node locally offers several benefits, including:

- **Increased privacy:** By using your own copy of the blockchain, you can ensure that your transactions are not being monitored by external nodes.
- **Faster synchronization:** With a local copy of the blockchain, you don't have to rely on external nodes for synchronization, resulting in faster and more reliable syncing.
- **Custom configurations:** You have complete control over the configuration of your Monero node, allowing you to tailor it to your specific needs.

> [!NOTE]
> You can also run the Docker image on a NAS (Network Attached Storage) to maintain a synchronized blockchain at all times.

## Build

To build the Monero node Docker image, follow these steps:

1. Clone the Monero node repository:

    ```shell
    git clone https://github.com/ds160/monero-node.git
    ```

2. Navigate into the cloned directory:

    ```shell
    cd monero-node
    ```

3. Build the Docker image:

    ```shell
    docker build -t monero-node .
    ```

4. Run the Docker container:

    ```shell
    docker run -d --name monero-node -p 18080:18080 -p 18081:18081 -v ${PWD}/path/to/store/blockchain:/root/.bitmonero monero-node
    ```

    This command starts the Monero node container, exposes the necessary ports for communication, and stores the blockchain at the specified path.

5. Verify that the node is running:

    ```shell
    docker logs monero-node
    ```

    You should see logs indicating that the node has successfully started.

That's it! You now have a Monero node running locally with your own copy of the blockchain.

## Create Monero GUI Wallet

To create and connect a Monero GUI Wallet to your locally running Monero node in Advanced mode, follow these steps:

1. Open the Monero GUI Wallet on your computer.

2. Click on the **Change wallet mode** button on the Welcome page.

3. On the mode Selection page, select **Advanced mode**.

4. Back on the Welcome page, click on the **Create a new wallet** button.

5. Choose a name and location for your wallet. Click **Next** to proceed.

6. Write down your recovery seed and click **Next**.

7. Verify your recovery phrase, select **Next**.

8. Give your wallet a strong password and confirm it. Click **Next** to proceed.

9. Connect to a remote node and add the remote node with following information:
    - **Address:** The IP address or hostname of your NAS or `localhost`.
    - **Port:** `18081` (or the port you have mapped on your NAS).

    Click **Next**.

10. Check the configuration and click **Create wallet**.

11. Enter your wallet password to unlock the wallet.

Congratulations! You have successfully connected the Monero GUI Wallet to your running Monero node.
