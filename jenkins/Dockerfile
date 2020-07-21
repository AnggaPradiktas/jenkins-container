FROM jenkins/jenkins

ENV JENKINS_USER admin
ENV JENKINS_PASS admin

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY plugins.txt /usr/share/jenkins/plugins.txt
COPY einit /usr/local/bin/einit

RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

USER root

ENTRYPOINT ["/usr/local/bin/einit"]

CMD ["/sbin/tini", "--", "/usr/local/bin/jenkins.sh"]