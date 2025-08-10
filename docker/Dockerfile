FROM debian:bullseye-slim

ENV DEBIAN_FRONTEND=noninteractive

RUN echo "path-exclude /usr/share/man/*" >> /etc/dpkg/dpkg.cfg.d/excludes && \
    echo "path-exclude /usr/share/doc/*" >> /etc/dpkg/dpkg.cfg.d/excludes && \
    echo "path-exclude /usr/share/locale/*" >> /etc/dpkg/dpkg.cfg.d/excludes && \
    dpkg --add-architecture i386 && \
    apt update && \
    apt install -y --no-install-recommends \
        gcc:i386 g++:i386 \
        make ccache \
        libstdc++6:i386 \
        curl git ca-certificates && \
    apt clean && \
    curl -L -o premake.tar.gz https://github.com/RaphaelIT7/gmod-common-module-base/releases/download/Premake-beta-07/premake5-linux.tar.gz && \
    tar -xvf premake.tar.gz --directory=/usr/bin && \
    chmod +x /usr/bin/premake5 && \
    rm -f premake.tar.gz && \
    gcc --version && \
    strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX && \
    rm -rf /var/lib/apt/lists/* /usr/share/* /usr/sbin/* /var/cache/* /var/log/* /var/tmp/* /var/lib/dpkg/info/* && \
    gcc --version && \
    strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX

ENV CC="ccache gcc"
ENV CXX="ccache g++"
ENV PATH="/usr/lib/ccache:$PATH"
ENV CCACHE_COMPILERCHECK=content
ENV CCACHE_SLOPPINESS=time_macros,include_file_mtime,include_file_ctime,pch_defines
ENV CCACHE_LOGFILE="/tmp/ccache.log"
ENV CCACHE_VERBOSE=1
ENV CCACHE_DEBUG=1

RUN ccache -M 1G && ccache -z


COPY entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

CMD ["/bin/bash"]