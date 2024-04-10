# Simple Docker Interface

This repository is a simplified interface for working with Docker, based on the example from the [Laradock] project (https://github.com/laradock/laradock ). We have cut out rarely used configurations to make the process of configuring and using Docker easier.

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/impelevin/sdi.git myproject
    ```

2. Go to the `myproject` directory:

    ```bash
    cd myproject
    ```

3. Copy the configuration files:

    ```bash
    cp .env.example .env
    cp docker-compose.example.yml docker-compose.yml
    ```

4. Edit the .env file and docker-compose as you need

5. Launch Docker compose:

    ```bash
    docker-compose up -d
    ```

## Using

Now you have a Docker work environment. You can start working with containers and develop your application.
```bash
docker-compose exec -u laradock app bash
```

## How to contribute

If you have suggestions for improvements or bug fixes, please create an issue or pull request. We welcome any constructive suggestions.

## License

This project is licensed under the MIT License - for details, see the [LICENSE](LICENSE) file.