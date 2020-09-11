# GADSProject

# Google Cloud Fundamentals: Getting Started with Compute Engine

# using cloud shell to Create A VM INSTANCE using the following parameters; vm name = my-vm-1, region=us-central1, Zone= us-central1-a, machine type=e2-, boot-disk=Debian GNU/Linux 9 (stretch), firewall= http traffic

gcloud beta compute --project=qwiklabs-gcp-00-c6e5d4a3fcf4 instances create my-vm-1 --zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM --maintenance-policy=MIGRATE --service-account=640485172902-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --tags=http-server --image=debian-9-stretch-v20200910 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=my-vm-1 --reservation-affinity=any && gcloud compute --project=qwiklabs-gcp-00-c6e5d4a3fcf4 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server

# display a list of all the zones in the region

gcloud compute zones list | grep us-central1

#chosing a zone from the list using gcloud config set compute/zone
gcloud config set compute/zone us-central1-b

# creating another VM instance called my-vm-2 in that zone, execute this command:

gcloud compute instances create "my-vm-2" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image "debian-9-stretch-v20190213" \
--subnet "default"

# closing the cloud shell

exit

# connecting between VM instances

In the Navigation menu (Navigation menu), click Compute Engine > VM instances.

You will see the two VM instances you created, each in a different zone.

Notice that the Internal IP addresses of these two instances share the first three bytes in common. They reside on the same subnet in their Google Cloud VPC even though they are in different zones.

To open a command prompt on the my-vm-2 instance, click SSH in its row in the VM instances list.

# using the ping command to confirm connection between the two instances created

ping my-vm-1

Press Ctrl+C to abort the ping command.

# Using the ssh command to open a command prompt on my-vm-1:

ssh my-vm-1

# installing nginx webserver on vm-1 instance

sudo apt-get install nginx-light -y

# opening the text editor using the nano command

sudo nano /var/www/html/index.nginx-debian.html

# editing the web server page

use the arrow key to manipulate some values
contl + o to save and cntl+X to exit the editor

# to confirm the webserver is serving to a new page

curl http://localhost/

# to exit the command prompt on vm-1

exit

# confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2

curl http://my-vm-1/

# from the console you can confirm that the web page is fine

click on the external IP address link from the console terminal
