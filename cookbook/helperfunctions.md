# Hilfsfunktionen in Contao

Contao bringt Funktionen mit, die es dem Entwicker ermöglichen schneller und effizenter zu arbeiten. Dazu gehören folgende Funktionen:

## Array Funktionen

### array_insert

### array_duplicate

### array_move_up

### array_move_down

### array_delete

## String Funktionen
### specialchars

### standardize
Standartisiert einen String. Dabei werden Leerzeichen durch Minuszeichen 
ersetzt.
```{.php}
echo standardize('Contao Open Source Content Management System');
// Ausgabe
contao-open-source-content-management-system
```

### deserialize($varValue, $blnForceArray=false)
Gibt ein unserialisiertes Array zurück.
```{.php}
$array = deserialize('a:1:{s:3:"foo";s:3:"bar";}');
 
// Ausgabe
Array
(
   [foo] => bar
)
```

Oder das Argument.
```{.php}
$array = deserialize(a:0:{}, true);
 
// Ausgabe, wenn das Array nicht leer ist
if (!empty($array))
{
    return;
}
```
### strip_insert_tags($strString)
Diese Funktion macht nicht das was der Name vermuten lässt, sondern 
ersetzt nicht die Inserttags von Contao, sondern entfernt sie.

```{.php}
echo strip_insert_tags('Hallo {{user::name}}!');
 
// Ausgabe
Hallo !
```

### trimsplit($strPattern, $strString)
Zerlegt eine Zeichenkette in Fragmente und entfernt gleichzeitig die 
Leerzeichen. Als Rückgabewert erhält man eine Array.

```{.php}
$string = 'Dieses; ist ;eine ; Zeichenkette ';
$trimsplit = trimsplit(';', $string);
 
// Ausgabe
Array
(
   [0] => Dieses
   [1] => ist
   [2] => eine
   [3] => Zeichenkette
)
```

### ampersand($strString, $blnEncode=true)
Konvertiert einen Sting nach der HTML Formatierung oder encodiert den Wert.

```{.php}
echo ampersand('contao/main.php?do=article&act=edit&id=1');
// Ausgabe 
contao/main.php?do=article&act=edit&id=1
```
 
## Sonstiges 

### scan($strFolder, $blnUncached=false)
Durchsucht den angegebenen Ordner nach Dateien und Unterordnern und gibt
die gefundenen Ergebnisse als Array zurück.

```{.php}
$arrFiles = scan(TL_ROOT . '/files');
 
// Ausgabe
Array
(
    [0] => music_academy
    [1] => tiny_templates
    [2] => tinymce.css
)
```

### log_message($strMessage, $strLog='error.log')
Mit dieser Funktion kann eine Nachricht in ein Logfile geschrieben werden. 
Per default wird dabei die error.log verwendet.

```{.php}
if($blnError)
{
  log_message
  (
    'Seit dem 18.11.2013 ist der LTS Support für Contao 2.11 eingestellt.'
  );
}

// Ausgabe
[18-Nov-2013 00:00:01] Seit dem 18.11.2013 ist der LTS Support für Contao 2.11 eingestellt.
```
### die_nicely($strTemplate, $strFallback)
Mit dieser Funktion kann man nach einem Fehler sauber aussteigen und ein 
dafür bereitgestelltes Template aufrufen.

```{.php}
if($blnError)
{
  die_nicely
  (
    'be_error', 
    'Es ist ein Fehler im ... aufgetreten, um diesen zu beheben gehen Sie wie folgt vor ....'
  );
}
```
