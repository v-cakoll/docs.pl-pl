---
title: Parametry połączenia w ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 02fe8d984f1287673477bb142b3f9626e248898e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363748"
---
# <a name="connection-strings-in-adonet"></a>Parametry połączenia w ADO.NET

Parametry połączenia zawierają informacje inicjujące, które są przesyłane jako parametr z dostawcy danych do źródła danych. Dostawca danych odbiera parametry połączenia jako wartość <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> właściwości. Dostawca analizuje parametry połączenia i sprawdza, czy składnia jest poprawna i czy słowa kluczowe są obsługiwane. <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> Następnie metoda przekazuje przeanalizowane parametry połączenia do źródła danych. Źródło danych wykonuje dalsze walidacje i nawiązuje połączenie.

## <a name="connection-string-syntax"></a>Składnia parametrów połączenia

Parametry połączenia to rozdzielana średnikami lista par parametrów klucz/wartość:

```
keyword1=value; keyword2=value;
```

W słowach kluczowych nie jest rozróżniana wielkość liter. Jednak w zależności od źródła danych w wartościach może być rozróżniana wielkość liter. Oba słowa kluczowe i wartości mogą zawierać [znaki odstępu](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Odstępy wiodące i końcowe są ignorowane w słowach kluczowych i w wartościach bez cudzysłowów.

Jeśli wartość zawiera średnika, [znaki kontrolne Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)lub wiodące lub końcowe biały znak, musi być ujęta w znaki pojedynczego lub podwójnego cudzysłowu. Na przykład:

```
Keyword=" whitespace  ";
Keyword='special;character';
```

Otaczający znak może nie występować w wartości, którą on należy. W związku z tym, wartość zawierająca znaki pojedynczego cudzysłowu może być ujęta tylko w znaki podwójnego cudzysłowu i odwrotnie:

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Możesz również wprowadzić znak ucieczki, używając dwóch z nich jednocześnie:

```
Keyword="double""quotation";
Keyword='single''quotation';
```

Cudzysłowy, a także znak równości, nie wymagają ucieczki, dlatego następujące parametry połączenia są prawidłowe:

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Ponieważ każda wartość jest odczytana do następnego średnika lub końca ciągu, wartość w tym ostatnim przykładzie to `a=b=c`, a ostatni średnik jest opcjonalny.

Wszystkie parametry połączenia mają tę samą składnię podstawową opisaną powyżej. Zestaw rozpoznanych słów kluczowych zależy od dostawcy, ale został rozmieszczony w latach od wcześniejszych interfejsów API, takich jak *ODBC*. Dostawca danych *.NET Framework* dla *SQL Server* (`SqlClient`) obsługuje wiele słów kluczowych ze starszych interfejsów API, ale zazwyczaj bardziej elastycznie i akceptuje synonimy dla wielu wspólnych słów kluczowych parametrów połączenia.

Wpisywanie błędów może spowodować błędy. Na przykład, `Integrated Security=true` jest prawidłowy, ale `IntegratedSecurity=true` powoduje błąd.

Parametry połączenia tworzone ręcznie w czasie wykonywania z niezweryfikowanych danych wejściowych użytkownika są narażone na ataki przez iniekcję ciągów i zagrażają bezpieczeństwu w źródle danych. Aby rozwiązać te problemy, w *ADO.NET* 2,0 wprowadzono [konstruktory parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md) dla każdego dostawcy danych *.NET Framework* . Te konstruktory parametrów połączenia uwidaczniają parametry jako właściwości o jednoznacznie określonym typie i umożliwiają sprawdzanie poprawności parametrów połączenia przed ich wysłaniem do źródła danych.

## <a name="in-this-section"></a>W tej sekcji

[Konstruktory parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md)\
Pokazuje, `ConnectionStringBuilder` w jaki sposób używać klas do konstruowania prawidłowych parametrów połączenia w czasie wykonywania.

[Parametry połączenia i pliki konfiguracji](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
Pokazuje, jak przechowywać i pobierać parametry połączenia w plikach konfiguracyjnych.

[Składnia parametrów połączenia](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
Opisuje sposób konfigurowania parametrów połączenia specyficznych dla dostawcy dla `SqlClient` `OleDb`, `OracleClient`, i `Odbc`.

[Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
Demonstruje techniki ochrony informacji używanych do nawiązywania połączenia ze źródłem danych.

## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
