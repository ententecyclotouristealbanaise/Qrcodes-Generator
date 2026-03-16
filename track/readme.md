# Tracking ECTA

Dossier contenant les pages de redirection pour le tracking des QR codes.

## Fonctionnement

Les QR codes de type URL peuvent maintenant pointer vers `/track/` avant la destination finale.

Le flux est le suivant :

1. Le QR encode une URL de redirection du type `/track/?target=...&qr=...&ga=...`
2. La page `/track/` envoie un événement `qr_scan` à Google Analytics 4
3. L'utilisateur est redirigé vers la destination finale
4. La destination reçoit aussi des paramètres UTM (`utm_source=qr_code`, `utm_medium=offline`, `utm_campaign=qr_scan`, `utm_content=<qr_id>`)

## Paramètres attendus

- `target` : URL finale à ouvrir
- `qr` : identifiant unique du QR code
- `ga` : ID de mesure GA4, par exemple `G-XXXXXXXXXX`

## Limites

Le tracking de scan ne fonctionne que pour les QR codes de type URL.

Les QR codes de type WiFi, vCard, SMS, téléphone, texte ou géolocalisation ne peuvent pas être mesurés dans Google Analytics sans page web intermédiaire.
