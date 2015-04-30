# Pays
## Consultation des pays

```json
[
  {
    "uuid":"urn:bossanova:country:35027c74-2e8c-48d0-94dc-f46133273e83",
    "label":"ACORES",
    "code":"P000000001",
    "updated_at":"2013-04-18T11:31:56Z"
  },
  {
    "uuid":"urn:bossanova:country:60809c88-d951-45bc-833b-55d4fc9fe195",
    "label":"AFGHANISTAN",
    "code":"P000000002",
    "updated_at":"2013-04-18T11:31:56Z"
  },
  {}
]

```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<countries type="array">
  <country>
    <uuid>urn:bossanova:country:35027c74-2e8c-48d0-94dc-f46133273e83</uuid>
    <label>ACORES</label><code>P000000001</code>
    <updated-at type="datetime">2013-04-18T11:31:56Z</updated-at>
  </country>
  <country>
    <uuid>urn:bossanova:country:60809c88-d951-45bc-833b-55d4fc9fe195</uuid>
    <label>AFGHANISTAN</label>
    <code>P000000002</code>
    <updated-at type="datetime">2013-04-18T11:31:56Z</updated-at>
  </country>
  <country> ... </country>
</countries>
```
Permet de récupérer la liste des pays.

### Habilitation

Type d’accès : Organizational unit (au moins 1)

Code habilitation : `bossanova/reflist/country/read_country`

### Requête HTTP

`GET /bossanova_tunnels/countries`

### Exemple d'appel

`curl http://fake.fr/synapse/countries.json?user_credentials=xxx`