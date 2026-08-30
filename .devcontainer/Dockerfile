FROM mcr.microsoft.com/devcontainers/typescript-node:4-24-bookworm

ARG GITLEAKS_VERSION=8.30.1
ARG TARGETARCH

RUN case "${TARGETARCH}" in \
      amd64) gitleaks_arch="x64" ;; \
      arm64) gitleaks_arch="arm64" ;; \
      *) echo "Unsupported architecture: ${TARGETARCH}" >&2; exit 1 ;; \
    esac \
    && gitleaks_archive="gitleaks_${GITLEAKS_VERSION}_linux_${gitleaks_arch}.tar.gz" \
    && curl --fail --location --silent --show-error --remote-name \
      "https://github.com/gitleaks/gitleaks/releases/download/v${GITLEAKS_VERSION}/${gitleaks_archive}" \
    && curl --fail --location --silent --show-error --remote-name \
      "https://github.com/gitleaks/gitleaks/releases/download/v${GITLEAKS_VERSION}/gitleaks_${GITLEAKS_VERSION}_checksums.txt" \
    && grep " ${gitleaks_archive}$" "gitleaks_${GITLEAKS_VERSION}_checksums.txt" | sha256sum --check - \
    && tar --extract --gzip --file "${gitleaks_archive}" --directory /usr/local/bin gitleaks \
    && rm "${gitleaks_archive}" "gitleaks_${GITLEAKS_VERSION}_checksums.txt"

USER node

RUN mkdir -p /home/node/.codex /home/node/.config/gh

USER root
