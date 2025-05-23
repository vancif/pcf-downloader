# Downloader PCF

## Descrizione
Il **Downloader** è un PowerApps Component Framework (PCF) che consente il download automatico di un file codificato in Base64 non appena il valore di uno specifico parametro cambia. Il controllo è utile per scenari in cui è necessario scaricare file generati dinamicamente all'interno di una PowerApp Canvas App oppure i cui dati binari vengono recuperati direttamente in canvas e non si dispone di un link di download a cui l'utente può collegarsi direttamente.

## Funzionalità
- Accetta una stringa Base64 che rappresenta il file da scaricare (completa di MIME Type)
- Utilizza un parametro per specificare il nome del file.
- Si attiva automaticamente al cambiamento di un parametro di trigger.

## Parametri
Il controllo utilizza tre parametri in ingresso:

| Nome       | Tipo   | Descrizione |
|------------|--------|-------------|
| `base64`   | String | Contenuto del file in formato Base64 (completo di MIME Type) |
| `name`     | String | Nome del file da assegnare al download. |
| `download` | String | Flag che attiva il download quando cambia valore. |


## Logica del Componente
- Il componente crea dinamicamente un elemento `<a>` con l'attributo `href` impostato sulla stringa Base64.
- Quando il valore di `download` cambia, il pulsante viene attivato automaticamente tramite `click()`, avviando il download. Il valore di `download` viene salvato per evitare attivazioni ripetute inutili. Per esempio, è possibile assegnare a `download` il valore di `Text(Now();"yyyy-mm-dd hh:mm:ss")` per triggerare il download.
- Il componente non ha volutamente UI, è completamente trasparente. Si raccomanda di **non nasconderlo** (lasciare la proprietà ```Visible``` su ```True```, altrimenti non funziona correttamente.

## Note
- Il controllo non esegue validazioni sui dati Base64. Assicurarsi che siano ben formattati.
- Il parametro `base64` deve essere completo di MIME Type, deve essere quindi qualcosa del tipo `data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAeIAAAJuCAIA...`
- Per sicurezza, i browser potrebbero bloccare i download automatici. Verificare le impostazioni del browser se il download non avviene.

