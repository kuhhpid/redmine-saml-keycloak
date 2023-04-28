FROM redmine:latest

ENV REDMINE_PLUGINS_MIGRATE true
ENV ADDITIONALS_VERSION 3.0.8
ENV REDMINE_SAML_VERSION 1.0.3

RUN apt-get update && apt-get -qq -y install curl

RUN cd /usr/src/redmine/

RUN curl -Lo additionals.tar.gz https://github.com/AlphaNodes/additionals/archive/refs/tags/$ADDITIONALS_VERSION.tar.gz
RUN curl -Lo redmine_saml.tar.gz https://github.com/AlphaNodes/redmine_saml/archive/refs/tags/$REDMINE_SAML_VERSION.tar.gz

RUN tar -xzf additionals.tar.gz
RUN tar -xzf redmine_saml.tar.gz
RUN mv additionals-$ADDITIONALS_VERSION plugins/additionals
RUN mv redmine_saml-$REDMINE_SAML_VERSION plugins/redmine_saml

RUN rm -f additionals.tar.gz
RUN rm -f redmine_saml.tar.gz

COPY saml-config.rb /usr/src/redmine/config/initializers/saml.rb

EXPOSE 3000