FROM centos:7.3.1611

ENV ANSIBLE_HOST_KEY_CHECKING=False
RUN curl -o /tmp/epel.rpm https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && rpm -ivh /tmp/epel.rpm \
    && rm -f /tmp/epel.rpm \
    && yum install -y ansible

# Allow manual test runners a nice alias for running their playbook
RUN echo "alias 'run'='ansible-playbook --skip-tags notest -i inventory main.yml'" >> /root/.bashrc

ONBUILD ARG ROLE_NAME
ONBUILD COPY ./example /ansible/
ONBUILD COPY ./ /ansible/roles/${ROLE_NAME}

ONBUILD WORKDIR /ansible
ONBUILD ENTRYPOINT [ "ansible-playbook" ]
ONBUILD CMD [ "--skip-tags", "notest", "-i", "inventory", "main.yml" ]

ENTRYPOINT [ "ansible" ]
CMD [ "-v" ]
