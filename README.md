# f5-bigip-declarative-waf-toolkit

*Python* script to manage *F5 Declarative WAF* policies. 

It can be used to:

1. Export a WAF policy in declarative format (JSON).
2. Export the *learning suggestions* for a WAF policy in declarative format (JSON).
3. Import a WAF policy from a policy file (JSON). Optionally, a suggestions file (JSON) can be specified in order to apply them. 
4. Export all WAF policies in declarative format (JSON).

# Working with F5 Declarative WAF

## Preparing environment variables

```
$export BIGIP_ADDRESS="X.X.X.X"
$export BIGIP_USERNAME="admin"
$export BIGIP_PASSWORD="admin"
```

## Exporting a WAF policy (--action 'export-waf-policy')

To export a WAF policy:

```
python f5-bigip-declarative-waf-toolkit.py --device $BIGIP_ADDRESS --username $BIGIP_USERNAME --password $BIGIP_PASSWORD --action export-waf-policy --policy /Common/asmpolicy_app1 --output ./tmp/asmpolicy_app1.json
```
```
[INFO]: Exporting WAF policy '/Common/asmpolicy_app1' to the file './tmp/asmpolicy_app1.json'.
[INFO]: WAF policy successfully exported.
```

To export a WAF policy using 'full' export mode (*--export-mode full*):

```
python f5-bigip-declarative-waf-toolkit.py --device $BIGIP_ADDRESS --username $BIGIP_USERNAME --password $BIGIP_PASSWORD --action export-waf-policy --policy /Common/asmpolicy_app1 --output ./tmp/asmpolicy_app1.json --export-mode full
```
```
[INFO]: Exporting WAF policy '/Common/asmpolicy_app1' to the file './tmp/asmpolicy_app1.json'.
[INFO]: WAF policy successfully exported.
```

To export a WAF policy in **debug** mode (*--log-level debug*):

```
python f5-bigip-declarative-waf-toolkit.py --device $BIGIP_ADDRESS --username $BIGIP_USERNAME --password $BIGIP_PASSWORD --action export-waf-policy --policy /Common/asmpolicy_app1 --output ./tmp/asmpolicy_app1.json --log-level debug
```
```
[INFO]: Exporting WAF policy '/Common/asmpolicy_app1' to the file './tmp/asmpolicy_app1.json'.
[DEBUG]: Retrieving WAF policies.
[DEBUG]: Starting new HTTPS connection (1): X.X.X.X:443
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/policies?$select=name,id,fullPath,link HTTP/11" 200 817
[DEBUG]: WAF policies successfully retrieved.
[DEBUG]: Running a 'export-policy' task.
[DEBUG]: https://X.X.X.X:443 "POST /mgmt/tm/asm/tasks/export-policy HTTP/11" 201 598
[DEBUG]: Waiting for the 'export-policy' task to complete.
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/tasks/export-policy/2lFc6cXjd5ZL-z9zwUqQiw HTTP/11" 200 646
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/tasks/export-policy/2lFc6cXjd5ZL-z9zwUqQiw HTTP/11" 200 646
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/tasks/export-policy/2lFc6cXjd5ZL-z9zwUqQiw HTTP/11" 200 646
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/tasks/export-policy/2lFc6cXjd5ZL-z9zwUqQiw HTTP/11" 200 646
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/tasks/export-policy/2lFc6cXjd5ZL-z9zwUqQiw HTTP/11" 200 779
[DEBUG]: The 'export-policy' task completed successfully.
[DEBUG]: Downloading the exported WAF policy.
[DEBUG]: https://X.X.X.X:443 "GET /mgmt/tm/asm/file-transfer/downloads/Common-asmpolicy_app1.json HTTP/11" 200 8541
[DEBUG]: WAF Policy successfully downloaded.
[DEBUG]: Saving WAF policy to file.
[DEBUG]: WAF Policy sucessfully saved to file.
[INFO]: WAF policy successfully exported.
```
