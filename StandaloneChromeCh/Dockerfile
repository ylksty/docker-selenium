# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# NOTE: DO *NOT* EDIT THIS FILE.  IT IS GENERATED.
# PLEASE UPDATE Dockerfile.txt INSTEAD OF THIS FILE
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
FROM selenium/node-chrome:3.4.0-einsteinium
LABEL authors=SeleniumHQ

USER root

# 配置中文语言
ENV LANGUAGE zh_CN.UTF-8
ENV LANG zh_CN.UTF-8
ENV LC_ALL=zh_CN.UTF-8
RUN  apt-get update -qqy \
  && /usr/share/locales/install-language-pack zh_CN \
  && locale-gen zh_CN.UTF-8 \
  && dpkg-reconfigure --frontend noninteractive locales \
  && apt-get -qqy --no-install-recommends install language-pack-zh-hans

# 安装基本字体
RUN  apt-get update -qqy \
  && apt-get -qqy --no-install-recommends install \
    fonts-ipafont-gothic \
    xfonts-100dpi \
    xfonts-75dpi \
    xfonts-cyrillic \
    xfonts-scalable

# 安装文泉驿微米黑字体
RUN  apt-get update -qqy \
  && apt-get -qqy install ttf-wqy-microhei \
  && ln /etc/fonts/conf.d/65-wqy-microhei.conf /etc/fonts/conf.d/69-language-selector-zh-cn.conf

# 设置时区
RUN echo "Asia/Shanghai" | tee /etc/timezone \
  && dpkg-reconfigure --frontend noninteractive tzdata

USER seluser

#====================================
# Scripts to run Selenium Standalone
#====================================
COPY entry_point.sh /opt/bin/entry_point.sh

EXPOSE 4444
