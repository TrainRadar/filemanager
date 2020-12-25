# PHP File Manager - Sprache: German/Deutsch
Der PHP File Manager ist ein hervorragendes Tool zur Ordner- und Dateiverwaltung, wenn ein SSH oder FTP Zugriff auf einen Webspace nicht gegeben ist.

![PHP File Manager](https://raw.github.com/TrainRadar/filemanager/master/aaaaa.PNG)

**ACHTUNG! Es ist nicht empfehlenswert, den File-Manager mit den Standard-Zugangsdaten in einem öffentlichen Verzeichnis zu betreiben. Dies kann zu erheblichen Sicherheitsproblemen führen. Falls ein schneller Einsatz angesetzt wird, ist zu empfehlen, die Datei nach dem Einsatz anderweitig vom Server zu entfernen.**

## Vorraussetzungen

- PHP Version 5.2 oder neuer.
- [ZIP PHP Erweiterung](http://php.net/manual/en/book.zip.php) für ZIP-Pack und ZIP Entpackungsverfahren. (In den meisten Webspaces vorhanden)
- Erweiterungen wie Fileinfo, iconv und mbstring. (Wichtig für die Grundsätzliche Funktion des Scripts, sind auch in den meisten Webspaces bereits vorhanden)

## Installationsprozess

Nach dem erfolgreichen Download der neusten Version, muss die Datei **filemaster.php** in einen beliebigen Ordner in einen Webspace verschoben werden. Anschließend kann die Datei (Standalone) im Browser geöffnet werden.
(Beispiel: localhost/admin/filemanager.php)


## Sicherheitsaspekte

Standard Benutzername/Passwort: **fm_admin** und **fm_admin**

**Achtung! Es ist empfehlenswert, eigene Zugangsdaten zu diesem Script zu vergeben, da die Standard-Benutzerdaten weitesgehend bekannt sind, und ein potenzielles Sicherheitsrisiko darstellen können!
Eine Änderung der Zugangsdaten kann in Zeile 10-13 in der Datei 'filemanager.php' vorgenommen werden.**

Um den Passwort-Schutz zu aktivieren oder deaktivieren, setze die variable '$use_auth' in Zeile 8 in der datei 'filemanager.php' auf 'true' (Aktiviert) oder 'false' (=Deaktiviert)

*Es ist empfehlenswert, dass der Webspace via HTTP Authentifizierung geschützt ist.*


## Benutzung in anderen Scripts

Es ist möglich, den Filemanager (Standalone) in anderen Scripts zu implementieren bzw. zu verwenden. Dies lässt sich einfach durch die Definition 'FM_EMBED' und anderer Variablen erreichen. Es folgt ein Beispiel einer Implementation aller wichtigen Variablen:

```php
class SomeController
{
    public function actionIndex()
    {
        define('FM_EMBED', true);
        define('FM_SELF_URL', UrlHelper::currentUrl()); // Muss deklariert werden, wenn die URL der Standalone-Datei des Filemanagers nicht gleich der URL des Skriptes ist!!
        require 'pfad/zu/filemanager.php';
    }
}
```

Mögliche Variablen zum Importieren:

- `FM_ROOT_PATH` - standardmäßig als `$_SERVER['DOCUMENT_ROOT']`
- `FM_ROOT_URL` - standardmäßig als `'http(s)://site.domain/'`
- `FM_SELF_URL` - standardmäßig als `'http(s)://site.domain/' . $_SERVER['PHP_SELF']`
- `FM_ICONV_INPUT_ENC` - standardmäßig als `'CP1251'`
- `FM_USE_HIGHLIGHTJS` - standardmäßig als `true`
- `FM_HIGHLIGHTJS_STYLE` - standardmäßig als `'vs'`
- `FM_DATETIME_FORMAT` - standardmäßig als `'d.m.y H:i'`


## Fehler

Für jegliche Art von Fehlerberichten und Fragen, stehe ich in folgendem Thread zur Verfügung 
[Issue tracker](https://github.com/TrainRadar/filemanager/issues).

## Lizensierung / Copyright

Die Software wurde ursprünglich von `alexantr` veröffentlicht, welcher das originale Repo jedoch leider archiviert hat. `alexantr` stellt das Skript unter der MIT-Lizenz zur Verfügung.

Die verwendeten Icons wurden von [Yusuke Kamiyamane](http://p.yusukekamiyamane.com/) erstellt.
