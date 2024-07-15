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

