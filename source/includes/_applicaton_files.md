# Prospects

## Description prospect
Attribut | Description | Format
--------- | ----------- | -----------
civility | Civilité | text [M., Mlle, Mme]
last_name | Nom de famille | text
first_name | Prénom | text
birthdate | Date de naissance | text jj/mm/aaaa
phone | N° de téléphone | text
phone_2 | N° de téléphone secondaire | text
email | Email | text
address_line_1 | Ligne d'adresse 1 | text
address_line_2 | Ligne d'adresse 2 | text
zip_code | Code postal | text
city | Ville | text
country_uuid | uuid du pays | text
nationality_uuid | uuid de la nationalité | text
prospect_study_level_uuid | uuid du niveau détude | text
prospect_initial_training_uuid | uuid de la formation de cours | text
spinneret | Filière | text
commercial_unit_uuid | uuid de l'UC | text
marketing_range_uuid | uuid de la gamme | text
marketing_curriculum_uuid | uuid du cursus commercial | text
teaching_unit_uuid | uuid du niveau commercial | text
marketing_option_uuid | uuid de l'option commerciale | text
rhythm_uuid | uuid du rythme | text
school_year | identifiant de l'exercice scolaire | text
effective_session_uuid | uuid de la session effective | text
source_kind | Type de la source | text [online, offline]
inserting_mode | Mode d'insertion | text [Automatique, Import fichier]
channel_capture_uuid | uuid du cannal de captation | text
origin | Provenance | text
description | Description | text
tracking_date | Date de tracking | text aaaa-mm-jj
prospect_qualification | ???? (contient des dates ou CHAUD ou nawak...) | text
commercial_unit_meeting_uuid | uuid de l'événement | text
paper_doc | Vrai si demande de documentation au format papier | boolean
geoip | @ IP | text

## Création d'un prospect

> En cas de succès de l'enregistrement, Synapse renvoie l'objet créé au format json.

```json
{
  "civility": "Mlle",
  "last_name": "Nom",
  "first_name": "Prénom",
  "phone": "0123456789",
  "email": "email@yopmail.com"
}
```

> Si une erreure est due à un problème lié aux paramètres application_file[xxx], on renvoie un tableau errors avec l’ensemble des erreurs au format json et le code html 422 (unprocessable entity).

> Si une erreur autre s’est produite lors de l’enregistrement, une erreur type est renvoyée au format de l’appel avec le code html qui convient.

Permet d’enregistrer une « demande » (nouveau signalement de prospect) dans Synapse.

### Habilitation

Type d’accès : Organizational unit (de niveau UC uniquement)

Code habilitation : `synapse/create_application_files`

### Requête HTTP

`POST /application_files`

Paramètre | Description 
--------- | ----------- 
application_file[nom_attribut] | Un [attribut](#description-prospect) du prospect
cookies[...] | Cookies si provient d'un formulaire html
geoip | @ IP 
drupal_id | Identifiant drupal 

### Exemple d'appel

`curl --data "application_file[civility]=Mlle&application_file[last_name]=Nom&application_file[first_name]=Prénom&application_file[phone]=0123456789&application_file[email]=email@yopmail.com" http://fake.fr/synapse/application_files.json`



## Création de N prospects

> En cas de succès de l'enregistrement, Synapse renvoie un tableau des objets en json créés en base.

```json
[
  {
    "civility": "Mlle",
    "last_name": "Nom",
    "first_name": "Prénom",
    "phone": "0123456789",
    "email": "email@yopmail.com"
  },
  {
    "civility": "M.",
    "last_name": "Bon",
    "first_name": "Jean",
    "phone": "0987654321",
    "email": "yopmail@email.com"
  }
]
```
> Si une erreure est due à un problème lié aux paramètres application_file[xxx], on renvoie un tableau errors avec l’ensemble des erreurs au format json et le code html 422 (unprocessable entity).

> Si une erreur autre s’est produite lors de l’enregistrement, une erreur type est renvoyée au format de l’appel avec le code html qui convient.

Permet d’enregistrer plusieurs « demandes » (nouveau signalement de prospect) dans Synapse en un seul appel.

### Habilitation

Type d’accès : Organizational unit (de niveau UC uniquement)

Code habilitation : `synapse/create_application_files`

### Requête HTTP

`POST /application_files/create_all`

Paramètre | Description 
--------- | ----------- 
application_file[n][nom_attribut] | Un [attribut](#description-prospect) du prospect n
cookies[...] | Cookies si provient d'un formulaire html
geoip | @ IP 
drupal_id | Identifiant drupal 

### Exemple d'appel

`curl --data "application_file[0][civility]=Mlle&application_file[0][last_name]=Nom&application_file[0][first_name]=Prénom&application_file[0][phone]=0123456789&application_file[0][email]=email@yopmail.com&application_file[1][civility]=M.&application_file[1][last_name]=Bon&application_file[1][first_name]=Jean&application_file[1][phone]=0987654321&application_file[1][email]=yopmail@email.com" http://fake.fr/synapse/application_files/create_all.json`

## Consultation des prospects

> Renvoie un tableau d’objets multi profondeurs

```json
[
  {
    "unformatted_created_at":"2013-01-31 11:04:27.144532",
    "civility":null,
    "last_name":"test_31012013_nom_1",
    "first_name":"test_31012013_florian_1",
    "phone":"test","phone_2":null,
    "email":"test_31012013_florian_1@yopmail.com",
    "address_line_1":null,
    "address_line_2":null,
    "zip_code":null,
    "city":null,
    "country_uuid":null,
    "birthdate":null,
    "nationality_uuid":null,
    "prospect_study_level_uuid":null,
    "prospect_initial_training_uuid":null,
    "spinneret":null,
    "description":null,
    "tracking_date":null,
    "prospect_qualification":null,
    "commercial_unit_uuid":"urn:bossanova:commercial_unit:e0b40795-ebcc-423b-a467-55dbfr0f671e",
    "marketing_range_uuid":"urn:bossanova:commercial_range:0e285884-4472-4e07-a77b-108fc0yhf7ce",
    "marketing_curriculum_uuid":"urn:bossanova:commercial_curriculum:409cbd30-1b47-4546-8d50-9ide4a2beccf8",
    "teaching_unit_uuid":"urn:bossanova:commercial_teaching_unit:24d831ce-c592-4827-856f-3adf6aeafa11",
    "marketing_option_uuid":null,
    "rhythm_uuid":null,
    "school_year":"2013",
    "effective_session_uuid":null,
    "commercial_unit_meeting_uuid":null,
    "paper_doc":false,
    "source_kind":"Online",
    "inserting_mode":"Automatique",
    "channel_capture_uuid":"urn:bossanova:prospect_capture_channel:40bb0be7-fe33-4k64-aaf6-c9118d81165d",
    "origin":null,
    "drupal_id":null,
    "geoip":null,
    "access_token":"xxx",
    "available_accesses":[],
    "created_at":"2013-01-31T11:04:27Z",
    "localization":{
                      "country": "France",
                      "state": null,
                      "city": "Paris",
                      "latitude": null,
                      "longitude": null
    },
    "parsed_cookie":{
                      "utmz":"101601107.1345539724.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none)",
                      "utma":"101601107.1295089060.1345539724.1358414005.1358431435.9",
                      "campaign_source":"(direct)",
                      "campaign_name":"(direct)",
                      "campaign_medium":"(none)",
                      "campaign_content":null,
                      "campaign_term":null,
                      "first_visit":"2012-08-21 09:02:04.000000",
                      "previous_visit":"2013-01-17 09:13:25.000000",
                      "current_visit_started":"2013-01-17 14:03:55.000000",
                      "times_visited":"9",
                      "gclid":null,
                      "status":"OK",
                      "proactivePrompt":null,
                      "proactiveEngaged":null,
                      "chatWith":null,
                      "first_page":null,
                      "mobile_detect":null
                    }
  },
  {}
]

```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<application-files type="array">
  <application-file>
    <unformatted-created-at>2013-01-31 11:04:27.144532</unformatted-created-at>
    <civility nil="true"/>
    <last-name>test_31012013_dupin_1</last-name>
    <first-name>test_31012013_florian_1</first-name>
    <phone>test</phone>
    <phone-2 nil="true"/>
    <email>test_31012013_florian_1@yopmail.com</email>
    <address-line-1 nil="true"/>
    <address-line-2 nil="true"/>
    <zip-code nil="true"/>
    <city nil="true"/>
    <country-uuid nil="true"/>
    <birthdate nil="true"/>
    <nationality-uuid nil="true"/>
    <prospect-study-level-uuid nil="true"/>
    <prospect-initial-training-uuid nil="true"/>
    <spinneret nil="true"/>
    <description nil="true"/>
    <tracking-date nil="true"/>
    <prospect-qualification nil="true"/>
    <commercial-unit-uuid>urn:bossanova:commercial_unit:e0b40795-ebcc-423b-a467-55dbe20f671e</commercial-unit-uuid>
    <marketing-range-uuid>urn:bossanova:commercial_range:0e285884-4472-4e07-a77b-108fc01df7ce</marketing-range-uuid>
    <marketing-curriculum-uuid>urn:bossanova:commercial_curriculum:409cbd30-1b47-4546-8d50-90e4a2beccf8</marketing-curriculum-uuid>
    <teaching-unit-uuid>urn:bossanova:commercial_teaching_unit:24d831ce-c592-4827-856f-3a066aeafa11</teaching-unit-uuid>
    <marketing-option-uuid nil="true"/>
    <rhythm-uuid nil="true"/>
    <school-year>2013</school-year>
    <effective-session-uuid nil="true"/>
    <commercial-unit-meeting-uuid nil="true"/>
    <paper-doc type="boolean">false</paper-doc>
    <source-kind>Online</source-kind>
    <inserting-mode>Automatique</inserting-mode>
    <channel-capture-uuid>urn:bossanova:prospect_capture_channel:40bb0be7-fe33-4584-aaf6-c9118d81165d</channel-capture-uuid>
    <origin nil="true"/>
    <drupal-id nil="true"/>
    <geoip nil="true"/>
    <access-token>yQVBTo5QqrTEZX5mka5</access-token>
    <available-accesses type="array"/>
    <created-at type="datetime">2013-01-31T11:04:27Z</created-at>
    <localization>
      <country>France</country>
      <state nil="true"/>
      <city>Paris</city>
      <latitude nil="true"/>
      <latitude nil="true"/>
    </localization>
    <parsed-cookie>
      <utmz>101601107.1345539724.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none)</utmz>
      <utma>101601107.1295089060.1345539724.1358414005.1358431435.9</utma>
      <campaign-source>(direct)</campaign-source>
      <campaign-name>(direct)</campaign-name>
      <campaign-medium>(none)</campaign-medium>
      <campaign-content nil="true"/>
      <campaign-term nil="true"/>
      <first-visit>2012-08-21 09:02:04.000000</first-visit>
      <previous-visit>2013-01-17 09:13:25.000000</previous-visit>
      <current-visit-started>2013-01-17 14:03:55.000000</current-visit-started>
      <times-visited>9</times-visited>
      <gclid nil="true"/>
      <status>OK</status>
      <proactivePrompt nil="true"/>
      <proactiveEngaged nil="true"/>
      <chatWith nil="true"/>
      <first-page nil="true"/>
      <mobile-detect nil="true"/>
    </parsed-cookie>
  </application-file>
  <application-file> ... </application-file>
</application-files>
```
Permet de lister l’ensemble des demandes de propsect contenues dans Synapse. Le résultat est limité à 200 enregistrements.

### Habilitation

Type d’accès : Organizational unit (de niveau UC uniquement)

Code habilitation : `synapse/application_files`

### Requête HTTP

`GET /application_files`

### Paramètres facultatifs

* `filter[created_after]=aaaa-mm-jj`

Permet de récupérer les demandes créées après la date (ou date time) précisée en paramètre.

Attend soit une date (ex : 2012-12-31) soit une date et heure (ex : 2012-12-11T19:37:24Z) soit un datetime non formatté (2013-01-24 10:16:13.067585)

### Exemple d'appel

`curl http://fake.fr/synapse/application_files.json?user_credentials=xxx&filter[created_after]=2014-11-03`
