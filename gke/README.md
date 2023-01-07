docker build -t chef-gke -f Dockerfile .


docker run -it -e GOOGLE_AUTH_SUPPRESS_CREDENTIALS_WARNINGS=true --rm -v ~/.config:/root/.config -v ~/.ssh:/root/.ssh -v $(pwd):/share chef-gke inspec-gke-cis-benchmark/run_profiles.sh    -c vdc -u dking -k foo -z us-central1-a -i /share/inputs.yml
