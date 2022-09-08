FROM python:3.9.7-slim

#
# Checkout token generator
#
RUN apt-get --yes update && \
    apt-get --no-install-recommends --yes install git && \
    pip install --upgrade pip && \
    pip install git+https://github.com/livmats/dtool-config-generator.git && \
    pip install gunicorn && \
    apt-get remove --purge --autoremove -y git && \
    rm -rf /var/lib/apt/lists/*

#
# Prepare application code
#
COPY compose/production/dtool_config_generator/production.cfg /

COPY compose/production/dtool_config_generator/start /start
RUN sed -i 's/\r//' /start
RUN chmod +x /start

# fix security policy for uni-freiburg rz ldap server
RUN sed -i "s/^CipherString = DEFAULT@SECLEVEL=2/CipherString = DEFAULT@SECLEVEL=1/" /usr/lib/ssl/openssl.cnf

ENTRYPOINT ["/start"]
CMD [""]
