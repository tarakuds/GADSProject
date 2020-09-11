# GADSProject

#GCP Fundamentals: Getting Started with Compute Engine

#creating A VM INSTANCE

gcloud beta compute --project=qwiklabs-gcp-03-97b7a7f36009 instances create my-vm-1

--zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM

--maintenance-policy=MIGRATE --service-account=228037526361-compute@developer.gserviceaccount.com

--scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append

--tags=http-server

--image=debian-9-stretch-v20200910

--image-project=debian-cloud

--boot-disk-size=10GB

--boot-disk-type=pd-standard

--boot-disk-device-name=my-vm-1
--reservation-affinity=any

gcloud compute --project=qwiklabs-gcp-03-97b7a7f36009 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server

#checking the list of instances
gcloud compute instance list
