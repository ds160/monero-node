# Monero Full Node

This Dockerfile provides a convenient way to run a Monero full node using your own copy of the blockchain. It gives you complete control over your Monero node.

## Overview

Running a Monero full node locally offers several benefits, including:

- **Increased privacy:** By using your own copy of the blockchain, you can ensure that your transactions are not being monitored by external nodes.
- **Faster synchronization:** With a local copy of the blockchain, you don't have to rely on external nodes for synchronization, resulting in faster and more reliable syncing.
- **Custom configurations:** You have full control over the configuration of your Monero node, allowing you to tailor it to your specific needs.

## Build

To build the Monero full node Docker image, follow these steps:

1. Clone the Monero full node repository:

    ```shell
    git clone https://github.com/ds160/monero-full-node.git
    ```

2. Navigate into the cloned directory:

    ```shell
    cd monero-full-node
    ```

3. Build the Docker image:

    ```shell
    docker build -t monero-full-node .
    ```

4. Run the Docker container:

    ```shell
    docker run -d --name monero-node -p 18080:18080 -p 18081:18081 -v ${PWD}/path/to/store/blockchain:/root/.bitmonero monero-full-node
    ```

    This command starts the Monero full node container, exposes the necessary ports for communication, and stores the blockchain at the specified path.

5. Verify that the node is running:

    ```shell
    docker logs monero-node
    ```

    You should see logs indicating that the node has successfully started.

That's it! You now have a Monero full node running locally with your own copy of the blockchain.

> [!NOTE]
> You can also run the Docker image on a NAS (Network Attached Storage) to maintain a synchronized blockchain at all times.

## Connect Monero GUI Wallet via Advanced Mode

To connect the Monero GUI Wallet to your locally running Monero full node in Advanced mode, follow these steps:

1. Open the Monero GUI Wallet on your computer.

2. Click on the **Settings** tab in the top menu bar.

3. In the settings menu, select **Wallet**.

4. Under the **Wallet Creation** section, click on the **Create Wallet** button.

5. Choose a name for your wallet and set a strong password. Click **Next** to proceed.

6. In the **Restore Wallet** section, select **Advanced mode** and click **Next**.

7. In the **Daemon Settings** section, select **Local Node (Recommended)**.

8. Enter the following information in the **Daemon Address** field:

    - **Host:** Enter the IP address or hostname of your NAS or `localhost`.
    - **Port:** `18081` (or the port you have mapped on your NAS).

9. Click **Connect** to establish a connection to your locally running Monero full node.

10. If the connection is successful, you will see a confirmation message. Click **Next** to proceed.

11. In the **Wallet File** section, choose a location to save your wallet file and click **Save**.

12. Enter your wallet password to unlock the wallet.

Congratulations! You have successfully connected the Monero GUI Wallet to your running Monero full node in Advanced mode.
