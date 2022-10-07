# Keycloak Authentication

### Build optimized keycloak image from Dockerfile:

If you intend to push it to ghcr:
`docker build . -t ghcr.io/<GH_USERNAME>/prebuilt_keycloak`

Otherwise (if you only want to use it locally):
`docker build . -t prebuilt_keycloak`

### Push built image to container registry:
1. `export CR_PAT=<GITHUB-PERSONAL-ACCESS-TOKEN>`
2. `echo $CR_PAT | docker login ghcr.io -u <GH-USERNAME> --password-stdin`
3. `docker push ghcr.io/<GH_USERNAME>/prebuilt_keycloak:latest`

Make sure to change the visibility of the package to public (per default private)
(make sure to exclude passwords from your built image)
(or perform ghcr-login on the machine which you want to use it on; as in Steps 1. & 2.):
https://docs.github.com/en/packages/learn-github-packages/configuring-a-packages-access-control-and-visibility#configuring-visibility-of-container-images-for-your-personal-account

### Start containers in dev-mode using:
`docker compose up -d`

