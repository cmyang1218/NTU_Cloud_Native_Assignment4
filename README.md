# NTU_Cloud_Native_Assignment4

## Folder Structure
```shell
.
├── app1.py
├── app2.py
├── Dockerfile.app1
├── Dockerfile.app2
└── README.md
```

## How to build the docker image

```shell
docker build -f ./Dockerfile.app1 -t cmyang1218/2025cloud:app1 .
docker build -f ./Dockerfile.app2 -t cmyang1218/2025cloud:app2 .
```

## How to run the docker container
```shell
docker run -it cmyang1218/2025cloud:app1 /bin/sh
docker run -it cmyang1218/2025cloud:app2 /bin/sh
```

## Docker Image/Tag Generation Design Flow

The following flowchart illustrates the overall logic for triggering Docker image generation and tag selection:

```mermaid
graph TD
    A[Code changes pushed to Version Control System (e.g., Git)] --> B{Is it the main branch (e.g., main, master)?};
    B -- Yes --> C{Does it include a version number change (e.g., modified version file)?};
    C -- Yes --> D[Read the new version number];
    D --> E{Is it a Release branch (e.g., release-x.y.z)?};
    E -- Yes --> F[Use the Release branch name as the Tag (e.g., x.y.z)];
    E -- No --> G[Use the first seven characters of the latest Commit SHA on the main branch as the Tag (e.g., <short_sha>)];
    C -- No --> G;
    B -- No --> H[Use the current branch name combined with the first seven characters of the latest Commit SHA as the Tag (e.g., <branch_name>-<short_sha>)];
    F --> I[Build and push Docker Image with the selected Tag];
    G --> I;
    H --> I;
    A --> J{Is it a Pull Request?};
    J -- Yes --> K[Use `pr-<PR_number>-<short_sha>` as the Tag];
    K --> I;
```
