# Creating a Virtual Machine || [GSP001](https://www.cloudskillsboost.google/focuses/3563?parent=catalog) ||

## # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

---
## ⚠️ **Disclaimer:**
#### This script and guide are provided for educational purposes to help you understand the lab process. Please ensure you understand the steps before using any scripts. Before using the script, I encourage you to open and review it to understand each step.The goal is to help you learn how to complete the labs effectively while following Qwiklabs' terms of service and YouTube's community guidelines.
---

### Run the following Commands in CloudShell

```
export ZONE=$(gcloud compute project-info describe \
--format="value(commonInstanceMetadata.items[google-compute-default-zone])")

export PROJECT_ID=$(gcloud config get-value project)

export PROJECT_NUMBER=$(gcloud projects describe ${PROJECT_ID} \
    --format="value(projectNumber)")

gcloud compute instances create gcelab \
    --project=$DEVSHELL_PROJECT_ID \
    --zone=$ZONE \
    --machine-type=e2-medium \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default \
    --metadata=enable-oslogin=true \
    --maintenance-policy=MIGRATE \
    --provisioning-model=STANDARD \
    --service-account=$PROJECT_NUMBER-compute@developer.gserviceaccount.com \
    --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/trace.append \
    --tags=http-server \
    --create-disk=auto-delete=yes,boot=yes,device-name=gcelab,image=projects/debian-cloud/global/images/debian-11-bullseye-v20241009,mode=rw,size=10,type=pd-balanced \
    --no-shielded-secure-boot \
    --shielded-vtpm \
    --shielded-integrity-monitoring \
    --labels=goog-ec-src=vm_add-gcloud \
    --reservation-affinity=any

gcloud compute instances create gcelab2 --machine-type e2-medium --zone=$ZONE

gcloud compute ssh --zone "$ZONE" "gcelab" --project "$DEVSHELL_PROJECT_ID" --quiet --command "sudo apt-get update && sudo apt-get install -y nginx && ps auwx | grep nginx "

gcloud compute firewall-rules create allow-http --network=default --allow=tcp:80 --target-tags=allow-http
```

## Congratulations ..!!🎉  You completed the lab shortly..😃💯

## *Well done..!* 👏

## Thank you for visiting.... :) 🗯️

## [Qwiklab_Explorers](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)

## Join to our community [Digital Dominators](https://linktr.ee/digital_dominators)
