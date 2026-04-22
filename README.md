# Docker-commands
troubleshoot commonds on docker
1. docker update
What It Does: Modify the resource limits of an existing container without needing to restart it.
Why It’s Useful: Adjust resources like CPU and memory on the fly to prevent slowdowns during peak usage, without causing downtime.
Usage Example:

docker update --cpus 2 --memory 1g <container_name>

Pro Tip: Increase resource limits during high-traffic periods and scale back afterward to optimize your system’s performance.

2. docker stats
What It Does: Displays live statistics on resource usage (CPU, memory, network) for all or specific running containers.
Why It’s Useful: Get real-time insights into container performance to identify resource hogs.
Usage Example:

docker stats <container_name>

Pro Tip: Use the --all flag to monitor every container on your system, not just the ones in the foreground.

3. docker diff
What It Does: Shows changes made to a container’s filesystem since it was started.
Why It’s Useful: Quickly identifies what files have been modified, added, or removed during runtime.
Usage Example:

docker diff <container_name>

Pro Tip: Use this to track unintentional changes in production containers and fix issues before committing new images.

4. docker commit
What It Does: Create a new image from the current state of a container.
Why It’s Useful: Snapshots the container state to capture changes for later use, ideal for iterative development or testing environments.
Usage Example:

docker commit <container_name> <new_image_name>

Pro Tip: Use this for testing different configurations, then save the successful state as a reusable image.

5. docker cp
What It Does: Copy files between the host system and a running container.
Why It’s Useful: Quickly retrieve logs or configuration files without interrupting the container.
Usage Example:

docker cp <container_name>:/path/to/file /host/path

Pro Tip: Use this when you need to access container files in real-time for troubleshooting.

6. docker build --squash
What It Does: Squashes all the image layers into one to minimize image size.
Why It’s Useful: Reduces the final image size, making deployments faster and saving storage space.
Usage Example:

docker build --squash -t <image_name> .

Pro Tip: Ideal for production images where reducing size is crucial for performance.

7. docker system df
What It Does: Provides a summary of disk usage by Docker images, containers, and volumes.
Why It’s Useful: Get an overview of your Docker system’s storage usage to identify space hogs.
Usage Example:

docker system df

Pro Tip: Run this command before performing a docker system prune to see how much disk space can be freed.

8. docker network inspect
What It Does: Provides detailed information about a Docker network, including connected containers and network settings.
Why It’s Useful: Crucial for debugging networking issues and container communication.
Usage Example:

docker network inspect <network_name>

Pro Tip: Use this command to verify if containers are correctly connected in multi-container setups.

9. docker exec -u
What It Does: Runs a command inside a container as a specified user.
Why It’s Useful: Helps you test container configurations and permissions, especially in security-sensitive environments.
Usage Example:

docker exec -u <user> <container_name> <command>

Pro Tip: Run commands as a non-root user for improved security during testing or debugging.

10. docker run --rm
What It Does: Automatically removes the container when it exits.
Why It’s Useful: Keeps your environment clean by removing temporary containers after they’ve finished their job.
Usage Example:

docker run --rm <image_name>

Pro Tip: Perfect for running tests or tasks that don’t require persistent containers.

11. docker-compose config
What It Does: Validates and displays the configuration of a docker-compose.yml file.
Why It’s Useful: Detects syntax errors and misconfigurations before they disrupt your workflow.
Usage Example:

docker-compose config

Pro Tip: Use this command to test configuration changes locally before deploying them to production.

12. docker rm -v
What It Does: Removes a container and its associated volumes.
Why It’s Useful: Frees up space by cleaning up unused containers and volumes.
Usage Example:

docker rm -v <container_name>

Pro Tip: Use this regularly to ensure that orphaned volumes don't consume unnecessary disk space.

13. docker export / docker import
What It Does: Exports a container’s filesystem as a tar archive and imports it back as a new image.
Why It’s Useful: Great for migrating containers between different environments or for archiving purposes.
Usage Example:

docker export <container_name> > container.tar
docker import container.tar <new_image_name>

Pro Tip: Use this to move container configurations from a development to production environment.

14. docker history
What It Does: Displays the history of an image, showing the creation date, size of layers, and commands that contributed to the image.
Why It’s Useful: Helps in optimizing Dockerfiles by identifying which commands added unnecessary size to the image.
Usage Example:

docker history <image_name>

Pro Tip: Use this to audit image efficiency and remove unnecessary layers or commands.

15. docker logs --since
What It Does: Retrieves logs from a container starting from a specific time.
Why It’s Useful: Focus on recent log entries, which is especially useful for debugging.
Usage Example:

docker logs --since "10m" <container_name>

Pro Tip: Great for pinpointing issues after a recent code change or deployment.

16. docker image prune
What It Does: Removes unused Docker images, freeing up disk space.
Why It’s Useful: Helps maintain a clutter-free environment by removing obsolete images.
Usage Example:

docker image prune

Pro Tip: Add the -a flag to remove all unused images, not just the dangling ones.

17. docker volume prune
What It Does: Cleans up unused Docker volumes.
Why It’s Useful: Removes orphaned volumes that take up space unnecessarily.
Usage Example:

docker volume prune

Pro Tip: Run this periodically to prevent unused volumes from accumulating.

18. docker events
What It Does: Streams real-time events from Docker’s server, such as container starts and stops.
Why It’s Useful: Stay on top of Docker activity for monitoring or debugging purposes.
Usage Example:

docker events

Pro Tip: Combine with grep to filter for specific events, like container terminations.

19. docker inspect --format
What It Does: Extracts specific information from docker inspect output in a custom format.
Why It’s Useful: Provides a more readable, concise view of Docker container or image data.
Usage Example:

docker inspect --format '{{ .Config.Env }}' <container_name>

Pro Tip: Ideal for automation scripts, extracting only the data you need.

20. docker build --no-cache
What It Does: Builds an image from scratch without using cache from previous builds.
Why It’s Useful: Guarantees a fresh build, especially useful when troubleshooting build issues.
Usage Example:

docker build --no-cache -t <image_name> .

Pro Tip: Use this when you want to avoid issues caused by outdated cache layers.

21. docker run -d
What It Does: Runs a container in detached mode, meaning it runs in the background.
Why It’s Useful: Keeps your terminal available while running long-lived containers.
Usage Example:

docker run -d <image_name>

Pro Tip: Ideal for background services like databases or web servers.

22. docker image inspect
What It Does: Provides detailed metadata about a Docker image, including its layers, environment variables, and build instructions.
Why It’s Useful: Useful for auditing and troubleshooting complex images.
Usage Example:

docker image inspect <image_name>

Pro Tip: Verify image integrity and ensure consistency in production environments.

23. docker save / docker load
What It Does: Save an image to a tar file and later load it back into Docker.
Why It’s Useful: Handy for transferring images between environments without needing internet access.
Usage Example:

docker save -o <image_name>.tar <image_name>
docker load -i <image_name>.tar

Pro Tip: Great for offline sharing of Docker images across teams or environments.

24. docker exec -it
What It Does: Runs an interactive command inside a container.
Why It’s Useful: Lets you interact with the container’s filesystem, ideal for debugging or manual configuration.
Usage Example:

docker exec -it <container_name> bash

Pro Tip: Use this for quick checks or modifying a running container’s state.

25. docker ps -q / docker stop $(docker ps -q)
What It Does: List container IDs and stops all running containers in one go.
Why It’s Useful: Quickly stop all running containers without specifying individual names.
Usage Example:

docker stop $(docker ps -q)

Pro Tip: Pair with docker rm $(docker ps -a -q) to clean up containers in one command.

26. docker exec --privileged
What It Does: Runs a command in a container with elevated privileges.
Why It’s Useful: Useful for troubleshooting or performing administrative tasks inside a container.
Usage Example:

docker exec --privileged <container_name> <command>

Pro Tip: Be cautious using this for security reasons as it grants elevated rights inside the container.

27. docker tag
What It Does: Tags an image with a new name, typically used for versioning images.
Why It’s Useful: Makes it easier to manage and deploy different versions of an image.
Usage Example:

docker tag <image_id> <repository>:<tag>

Pro Tip: Use this when pushing images to a repository to keep track of versions.

28. docker push
What It Does: Pushes an image to a remote repository (e.g., Docker Hub).
Why It’s Useful: Facilitates image sharing across environments or teams.
Usage Example:

docker push <repository>:<tag>

Pro Tip: Always ensure your repository is public or properly authenticated to avoid push errors.

29. docker login
What It Does: Logs into a Docker registry to authenticate and push images.
Why It’s Useful: Necessary for pushing images to private repositories or Docker Hub.
Usage Example:

docker login

Pro Tip: Use secure authentication methods like two-factor authentication for added security.

30. docker-compose up --build
What It Does: Builds and starts the containers defined in a docker-compose.yml file.
Why It’s Useful: Useful for rebuilding images and starting services in a single step.
Usage Example:

docker-compose up --build

Pro Tip: Use this when you've made changes to your Dockerfile or dependencies and need a fresh build.

Thanks for Reading!

I hope you found this article insightful and helpful. If you'd like to connect or discuss more on this topic, feel free to reach out on LinkedIn.
