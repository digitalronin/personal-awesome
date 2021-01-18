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

## Enable `make whatever [some parameter]`

From this [stackoverflow post](https://stackoverflow.com/a/14061796/794111)

e.g If the first argument is "newpost"...

```makefile
ifeq (newpost,$(firstword $(MAKECMDGOALS)))
  # use the rest as arguments for "newpost"
  POST_ARGS := $(wordlist 2,$(words $(MAKECMDGOALS)),$(MAKECMDGOALS))
  # ...and turn them into do-nothing targets
  $(eval $(POST_ARGS):;@:)
endif

.PHONY: newpost
newpost:
	cp -r template $(POST_ARGS)
```
