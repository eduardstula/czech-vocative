[![Latest Stable Version](http://poser.pugx.org/eduardstula/czech-vocative/v)](https://packagist.org/packages/eduardstula/czech-vocative)
[![Latest Unstable Version](http://poser.pugx.org/eduardstula/czech-vocative/v/unstable)](https://packagist.org/packages/eduardstula/czech-vocative)
![Run tests](https://github.com/eduardstula/czech-vocative/actions/workflows/run-tests.yml/badge.svg)
[![Total Downloads](http://poser.pugx.org/eduardstula/czech-vocative/downloads)](https://packagist.org/packages/eduardstula/czech-vocative)
[![License](https://poser.pugx.org/granam/czech-vocative/license)](https://packagist.org/packages/granam/czech-vocative)

# Vokativ

*Oslovte své uživatele správně!*

## Podporované verze PHP
- PHP 8.0
- PHP 8.1
- PHP 8.2
- PHP 8.3 (nightly)
- PHP 8.4 (nightly)

## Instalace

```bash
composer require eduardstula/czech-vocative
```

## Použití

```php
<?php
use Eduardstula\CzechVocative\CzechName;
$name = new CzechName();
$name->vocative('Petr'); // 'Petře'
$name->vocative('Novák'); // 'Nováku'
$name->vocative('Adriana');	// 'Adriano'
$name->vocative('Fialová');	// 'Fialová'
```

Metoda `vocative($name, $isWoman = null, $isLastName = null)` bere jako první argument vlastní jméno v 1. pádu jednotného čísla a vrátí ho vyskloňované v 5. pádu.
Upozorňujeme, že funkce nemusí fungovat správně pro jména cizího původu.

### Další volitelné argumenty jsou:

`$isWoman`

Použijte `true`, pokud si přejete zadané jméno skloňovat jako ženské.

Použijte `false`, pokud si přejete zadané jméno skloňovat jako mužské.

Ve výchozím případě `null` je pohlaví detekováno automaticky.

```php
<?php
use Eduardstula\CzechVocative\CzechName;

$name = new CzechName();
$name->vocative('Michel'); // 'Micheli' - automaticky jako mužské
$name->vocative('Michel', false); // 'Micheli - výslovně mužské'
$name->vocative('Michel', true); // 'Michel - výslovně ženské'
```

`$isLastName`

Použijte `true`, pokud si přejete zadané jméno skloňovat jako příjmení.

Použijte `false`, pokud si přejete zadané jméno skloňovat jako křestní jméno.

Ve výchozím případě `null` je typ jména detekován automaticky.

Hodnota tohoto parametru ovlivňuje pouze skloňování ženských jmen.

```php
<?php
use Eduardstula\CzechVocative\CzechName;

$name = new CzechName();
$name->vocative('Ivanova'); // 'Ivanova' - automaticky příjmení
$name->vocative('Ivanova', true, true); // 'Ivanova'
$name->vocative('Ivanova', true, false); // 'Ivanovo'
```

## Automatická detekce pohlaví

Knihovna **vokativ** poskytuje také jednoduchou funkci na detekci pohlaví podle křestního jména či příjmení.
Pro četnosti jmen v ČR podle [statistického úřadu](http://www.mvcr.cz/clanek/cetnost-jmen-a-prijmeni-722752.aspx)
funkce funguje správně v 99.7% případů.

```php
<?php
use Eduardstula\CzechVocative\CzechName;

$name = new CzechName();
$name->isMale('Michal'); // true
$name->isMale('Novák'); // true
$name->isMale('Tereza'); // false
$name->isMale('Nováková'); // false
```

## Credits
- Original Python version of this library [Mimino666/vokativ](https://github.com/Mimino666/vokativ/), author Michal Danilák.
- Reimplementation from Python to PHP 5.6 [bigit/vokativ](https://bitbucket.org/bigit/vokativ), author Petr Joachim.
- Port to PHP 8.0 and automatic tests [granam/czech-vocative](https://github.com/granam/czech-vocative), author Jaroslav Týc 