---
title: Parametry połączenia w ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 3b7cb0ab061da8364a9fecc3868ba9aaf7501577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881158"
---
# <a name="connection-strings-in-adonet"></a>Parametry połączenia w ADO.NET

Parametry połączenia zawierają informacje inicjowania, który jest przekazywany jako parametr od dostawcy danych do źródła danych. Dostawca danych otrzymuje parametry połączenia jako wartość <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> właściwości. Dostawca analizuje ciąg połączenia i zapewnia, że składnia jest poprawna i że słowa kluczowe są obsługiwane. A następnie <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> metoda przekazuje parametry przeanalizowany połączenia ze źródłem danych. Źródło danych dalsze przeprowadza weryfikację i nawiąże połączenie.

## <a name="connection-string-syntax"></a>Składnia ciągu połączenia

Ciąg połączenia jest rozdzielaną średnikami listę par klucz/wartość do parametru:

```
keyword1=value; keyword2=value;
```

Słowa kluczowe nie jest rozróżniana wielkość liter. Jednakże, wartości, może być uwzględniana jest wielkość liter, w zależności od źródła danych. Słowa kluczowe i wartości mogą zawierać [białych znaków](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Początkowe i końcowe biały jest ignorowany słów kluczowych i nienotowane wartości.

Jeśli wartość zawiera średnika, [znaków kontrolnych Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), lub wiodące lub końcowe biały znak, muszą być ujęte w pojedyncze lub podwójne znaki cudzysłowu. Na przykład:

```
Keyword=" whitespace  ";
Keyword='special;character';
```

Znak otaczającej nie wystąpi w wartość, która je otacza. Wartość zawierającą znaki pojedynczego cudzysłowu mogą być ujęte w związku z tym, tylko w znaki cudzysłowu i na odwrót:

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Znaki cudzysłowu, same, jak również równości, nie wymagają anulowania zapewnianego element, aby poniższe parametry połączenia są prawidłowe:

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Ponieważ każda wartość jest do odczytu do następnego średnika lub końca ciągu, wartości w drugim przykładzie jest `a=b=c`, i końcowy średnik jest opcjonalne.

Wszystkie ciągi połączenia współużytkować tę samą składnię podstawowe opisanych powyżej. Zbiór rozpoznane słowa kluczowe, jest zależna od dostawcy i został przekształcony w ciągu lat, za pomocą starszych interfejsów API, takich jak *ODBC*. *.NET Framework* dostawca danych dla *programu SQL Server* (`SqlClient`) obsługuje wiele słów kluczowych z interfejsów API starszych, ale jest zazwyczaj bardziej elastyczne i akceptuje synonimy dla wielu typowych parametrów połączenia słowa kluczowe.

Błędów może spowodować błędy. Na przykład `Integrated Security=true` jest prawidłowy, ale `IntegratedSecurity=true` powoduje błąd.

Parametry połączenia, tworzony ręcznie, w czasie wykonywania z danych wejściowych użytkownika niezweryfikowanych są narażone na ataki polegające na iniekcji ciągu i zagrozić zabezpieczeń w źródle danych. Aby rozwiązać te problemy *ADO.NET* 2.0 wprowadzono [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md) dla każdego *.NET Framework* dostawcy danych. Te Konstruktorzy parametrów połączeń ujawnić parametry jako silnie typizowane właściwości, dzięki czemu będzie można sprawdzić poprawność parametrów połączenia przed wysłaniem ich do źródła danych.

## <a name="in-this-section"></a>W tej sekcji

[Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)\
Pokazuje sposób użycia `ConnectionStringBuilder` klas do utworzenia prawidłowego połączenia ciągów w czasie wykonywania.

[Parametry połączenia i pliki konfiguracji](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
Pokazuje, jak przechowywać i pobierać parametry połączenia w plikach konfiguracji.

[Składnia ciągu połączenia](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
W tym artykule opisano jak skonfigurować parametry połączenia specyficzne dla dostawcy na potrzeby `SqlClient`, `OracleClient`, `OleDb`, i `Odbc`.

[Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
Pokazuje technik ochrony informacje używane do połączenia ze źródłem danych.

## <a name="see-also"></a>Zobacz także

- [Nawiązywanie połączenia ze źródłem danych](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
