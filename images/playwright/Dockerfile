FROM mcr.microsoft.com/playwright/python:v1.49.1-noble

# set sh to use bash by default
RUN ln -sf /bin/bash /bin/sh && \
    ln -sf /usr/bin/rename.ul /usr/bin/rename && \
# set timezone
    export TZ=Asia/Shanghai && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
# set path
    echo "export PATH=\"$PATH:/usr/local/bin\"" >> ~/.bashrc  && \
    echo "export LD_LIBRARY_PATH=\"/lib/x86_64-linux-gnu${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}\"" >> ~/.bashrc && \
    echo 'LD_LIBRARY_PATH="lib/x86_64-linux-gnu"' >> /etc/environment
    
RUN rm /etc/apt/apt.conf.d/docker-clean
RUN apt-get update && apt-get install -y wget npm vim cron inetutils-ping openssh-server \
    zlib1g-dev libbz2-dev  libbz2-dev libssl-dev libncurses-dev libsqlite3-dev libreadline-dev tk-dev libffi-dev gcc make \
    libxss1 libatspi2.0-0 libatk-bridge2.0-0 libxkbcommon-x11-dev libappindicator3-1 libu2f-udev \
# install fonts
    language-pack-zh* fonts-wqy-microhei fonts-wqy-zenhei fonts-noto-cjk \
# install java8
    openjdk-8-jdk \
# install opencv
    opencv* \
# install bison, gawk
    bzip2 texinfo g++ bison gawk \
# install certificates 
    ca-certificates && \
    apt-get autoremove -y && apt-get clean


RUN pip3 install --break-system-packages numpy pytest pytest-playwright uvicorn psutil fastapi service requests schedule