FROM lambci/lambda-base

RUN rm -rf /var/runtime /var/lang && \
  curl https://lambci.s3.amazonaws.com/fs/nodejs8.10.tgz | tar -zx -C /

COPY awslambda-mock.js /var/runtime/node_modules/awslambda/build/Release/awslambda.js

RUN curl -sL https://rpm.nodesource.com/setup_8.x | bash -

RUN yum install -y nodejs-8.10.0-1nodesource

USER sbx_user1051

ENTRYPOINT ["/usr/bin/node", "--expose-gc", "--max-semi-space-size=150", "--max-old-space-size=2707", \
  "/var/runtime/node_modules/awslambda/index.js"]

