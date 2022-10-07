# Keycloak Authentication

### Build optimized keycloak image from Dockerfile:

If you intend to push it to ghcr:
`docker build . -t ghcr.io/<GH_USERNAME>/prebuilt_keycloak`

Otherwise (if you only want to use it locally):
`docker build . -t prebuilt_keycloak`

### Push built image to container registry:
`export CR_PAT=<GITHUB-PERSONAL-ACCESS-TOKEN>`
`echo $CR_PAT | docker login ghcr.io -u <GH-USERNAME> --password-stdin`
`docker push ghcr.io/<GH_USERNAME>/prebuilt_keycloak:latest`

### Start containers in dev-mode using:
`docker compose up -d`

