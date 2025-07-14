FROM debian:bullseye-slim

ENV DEBIAN_FRONTEND=noninteractive

RUN echo "path-exclude /usr/share/man/*" >> /etc/dpkg/dpkg.cfg.d/excludes && \
    echo "path-exclude /usr/share/doc/*" >> /etc/dpkg/dpkg.cfg.d/excludes && \
    echo "path-exclude /usr/share/locale/*" >> /etc/dpkg/dpkg.cfg.d/excludes

RUN dpkg --add-architecture i386 && \
    apt update && \
    apt install -y --no-install-recommends \
        gcc:i386 g++:i386 \
        make ccache \
        libstdc++6:i386 \
        curl git ca-certificates && \
    apt clean && rm -rf /var/lib/apt/lists/*

ENV CC="ccache gcc"
ENV CXX="ccache g++"
ENV PATH="/usr/lib/ccache:$PATH"

RUN ccache -M 200M

COPY entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

CMD ["/bin/bash"]