# Tips & Tricks

Stuff I found useful, and wanted to save in a searchable form so I can find it
again when I need it.

## List DigitalOcean regions

```bash
curl -X GET -H "Content-Type: application/json" \
  -H "Authorization: Bearer ${TF_VAR_api_token}" \
  "https://api.digitalocean.com/v2/regions" \
  | jq '.regions[] | (.name + ", " +.slug)'
```

## Append to a file using sudo

```bash
echo "188.166.180.22  dokku.me" | sudo tee -a /etc/hosts
```
