FROM debian:8.3
MAINTAINER Arachnys <techteam@arachnys.com>

RUN echo 'deb http://debian.man.ac.uk/debian/ stable main contrib non-free' >> /etc/apt/sources.list

RUN apt-get -yq update && \
    apt-get -yq install \
        xvfb \
        libgtk2.0-0 \
        libgconf-2-4 \
        libXtst6 \
        libnss3 \
        libnotify4 \
        ttf-mscorefonts-installer \
        ttf-liberation \
        ttf-wqy-zenhei \
        ttf-unfonts-core \
        fonts-sil-padauk \
        fonts-lklug-sinhala \
        fonts-thai-tlwg \
    && apt-get -yq autoremove \
    && apt-get -yq clean \
    && rm -rf /var/lib/apt/lists/* \
    && truncate -s 0 /var/log/*log

ADD build/athenapdf-linux-x64/ /athenapdf/
WORKDIR /athenapdf/

ENV PATH /athenapdf/:$PATH

ADD entrypoint.sh /athenapdf/entrypoint.sh

RUN mkdir -p /converted/
WORKDIR /converted/

CMD ["athenapdf"]

ENTRYPOINT ["/athenapdf/entrypoint.sh"]
