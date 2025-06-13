## Setting Up

1. Navigate to [se-symbiota-private](https://github.com/BU-Spark/se-symbiota-private) and copy all files/directories excluding the `containers` directory.
2. Navigate to [se-symbiota](https://github.com/BU-Spark/se-symbiota) and paste all files/directories within the root directory.
3. Go to the terminal and within the `se-symbiota` repository, navigate to the appropriate branch. Now navigate to the containers directory.
```
cd containers
```
Then run the following:
```
docker compose up --build
```
You might have to run the following first:
```
docker network create symbiota-network
```