# EPOST API

## Send API

## Endpoints
prod: https://send.api.epost.de
dev: https://send.api.epost-gka.de

`POST /letters` Entwurf mit Metadaten, Anschreiben und Anhängen erstellen: POST /letters
`POST /deliveries` Entwurf versenden: POST /deliveries
`DELETE /letters/{letterId}`Entwurf löschen: 
`POST /postage-info` Preis für Entwurf abfragen
`POST /postage-info` Preisinformationen abfragen

### Create DRAFT

#### Special Endpoints
prod  `POST https://mailbox.api.epost.de/letters`
dev   `POST https://mailbox.api.epost-gka.de/letters`


#### Example (physical letter)
    POST https://mailbox.api.epost.de/letters HTTP/1.1
    x-epost-access-token: <E-POST Access Token>
    Content-Type: multipart/mixed; boundary="Boundary_8d16804cd7f91e6"
    Host: mailbox.api.epost.de
    --Boundary_8d16804cd7f91e6
    Content-Type: application/vnd.epost-letter+json
    {
      "envelope": {
        "letterType": {
          "systemMessageType": "hybrid"
        },
        "recipientsPrinted": [
          {
            "addressAddOn": "3. Stock",
            "city": "",
            "company": "Deutsche Post AG",
            "firstName": "Max",
            "houseNumber": "14",
            "lastName": "Mustermann",
            "postOfficeBox": "",
            "salutation": "Herr",
            "streetName": "Musterstr. 3",
            "title": "Dr.",
            "zipCode": "53115"
    } ],
        "sender": {
          "displayName": "Max Mustermann",
          "epostAddress": "max.mustermann@musterfirma.epost.de"
        },
        "subject": "Test erfolgreich"

#### Headers

##### Gesamte Nachricht
    Content-Type: multipart/mixed; boundary

##### Meta Data
    Content-Type: application/vnd.epost-letter+json

##### Anschreiben
    Content-Type: text/html

##### Anhang
    Content-Type: application/pdf

##### General
    Content-Transfer-Encoding: base64 (/binary)

#### Response
  `201` - created
  `400`, `403`, `413`


### Send Draft



## Other
Für einen erleichterten Einstieg und erste Tests zeigen sowohl die Code Beispiele, als auch die Dokumentation die Möglichkeit des Direktversandes eines E-POSTBRIEFES über die E-POSTBUSINESS API. Ich möchte Sie hiermit gerne frühestmöglich darauf hinweisen, sich am Verfahren zu orientieren, zuerst den Entwurf eines Briefes anzulegen und diesen anschließend über die zurückgelieferte Referenz zu versenden. Die Möglichkeit des Direktversandes wird auf mittellange Sicht nicht weiterentwickelt.


Wie Sie sicherlich im Partnerportal gelesen haben, werden wir im Anschluss an die Entwicklung Ihre Applikation abnehmen und zertifizieren. Hierfür sollten Sie im Anschluss der Entwicklung noch Zeit einplanen. Weiterhin benötigen Sie im Rahmen der Zertifizierung einen produktiven E-POST Account. Sollten Sie das Anmeldeverfahren „Resource Owner Password Credentials Grant“ zur Anmeldung verwenden wollen, benötigen wir zusätzlich im Rahmen der Abnahme ein Sicherheitskonzept.
Bitte geben Sie mir kurz Bescheid, ob Sie dieses Verfahren nutzen möchten, dann sende ich Ihnen die entsprechenden Unterlagen zu.
