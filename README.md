# Remove-Orphan-Projects-in-Jenkins
Remove Orphan Projects in Jenkins

>Orphan-Projects in Jenkins means the once you have deleted in Jenkins's side but still existing in the host where Jenkins is running

Run the below command
```bash
for ws in /var/lib/jenkins/workspace/*/; do
  job=$(basename "$ws" | sed 's/@[0-9]*$//')
  if [ ! -d "/var/lib/jenkins/jobs/$job" ]; then
    echo "Deleting: $ws"
    sudo rm -rf "$ws"
  fi
done
```
