FROM chef/inspec:4.41.2
RUN apt-get update && apt-get install -y make gcc g++
RUN ln -s /bin/mkdir /usr/bin/mkdir  # gem wants this for inexplicable reasons
RUN gem install inspec-bin -v 4.41.2 --no-document --quiet
RUN gem install train-kubernetes

WORKDIR /
RUN git clone https://github.com/GoogleCloudPlatform/inspec-gke-cis-benchmark.git
RUN cd inspec-gke-cis-benchmark && bundle install
RUN apt-get update && apt-get install -y jq curl python3
RUN curl https://sdk.cloud.google.com | bash
RUN ln -s /root/google-cloud-sdk/bin/gcloud /usr/bin/gcloud
ENV CHEF_LICENSE=accept
RUN inspec plugin install train-kubernetes
ENTRYPOINT []