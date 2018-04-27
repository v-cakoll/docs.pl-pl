---
title: Rozszerzanie i zwężanie konwersji (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 960b4e4c7184309b6a84247d86fb94ccb2faf877
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozszerzanie i zwężanie konwersji (Visual Basic)
Ważną kwestią konwersji typu to, czy wynik konwersji jest spoza zakresu docelowego typu danych.  
  
 A *rozszerzanie konwersji* zmiany wartości na typ danych, które można zezwolić na wszystkie możliwe wartości oryginalnych danych.  Rozszerzanie konwersji zachować wartość źródła, ale można zmienić jej reprezentacji. W takim przypadku konwersji z typu całkowitego `Decimal`, lub z `Char` do `String`.  
  
 A *konwersja zawężająca* zmiany wartości na typ danych, który może nie posiadać pewnych możliwych wartości. Na przykład zostać zaokrąglona wartość ułamkową konwertowania na typ całkowity, a następnie konwertowana na typ liczbowy `Boolean` zostanie zmniejszona do jednej `True` lub `False`.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli przedstawiono standardowe rozszerzanie konwersji.  
  
|Typ danych|Rozszerzenie do typów danych <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[krótki](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Liczba całkowita](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Uinteger —](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[długa](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Pojedynczy](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Wszelkie typ wyliczeniowy ([wyliczenia](../../../../visual-basic/language-reference/statements/enum-statement.md))|Jego podstawowym typem całkowitym i dowolnego typu, do którego rozszerzenie typu bazowego.|  
|[char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` Tablica|`Char` Tablica, `String`|  
|Dowolnego typu|[Obiekt](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Dowolnego typu pochodnego|Podstawowa dowolnego typu, z którego pochodzi <sup>3</sup>.|  
|Dowolnego typu|Interfejs, który implementuje.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Typ danych lub typ obiektu.|  
  
 <sup>1</sup> zgodnie z definicją każdego typu danych rozszerzenie do samej siebie.  
  
 <sup>2</sup> konwersje z `Integer`, `UInteger`, `Long`, `ULong`, lub `Decimal` do `Single` lub `Double` może spowodować utratę dokładności, ale nigdy nie utratę wielkości. W tym sensie nie wiążą się utracie danych.  
  
 <sup>3</sup> może wydawać się zaskakująco, że jest rozszerzanie konwersji z typu pochodnego do jednego z jego typów podstawowych. Uzasadnienie jest typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego, więc go, zaliczamy do wystąpienia typu podstawowego. W przeciwnym kierunku typu podstawowego nie zawiera żadnych nowych elementów członkowskich zdefiniowanych przez typ pochodny.  
  
 Rozszerzanie konwersji zawsze pomyślnie w czasie wykonywania i nigdy nie pociągnąć za sobą utraty danych. Zawsze je wykonać niejawnie, czy [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia typ sprawdzania przełącznik `On` lub `Off`.  
  
## <a name="narrowing-conversions"></a>Zawężanie konwersji  
 Następujące standardowych konwersji zawężającej:  
  
-   Odwrotnej kierunków rozszerzającą konwersje w poprzednim tabeli (z wyjątkiem tego, że każdy typ rozszerzenie do samego siebie)  
  
-   Konwersje w obu kierunkach między [logiczna](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) i dowolnego typu numerycznego  
  
-   Konwersje z dowolnego typu liczbowego do dowolnego typ wyliczeniowy (`Enum`)  
  
-   Konwersje w obu kierunkach między [ciąg](../../../../visual-basic/language-reference/data-types/string-data-type.md) i dowolnego typu liczbowego, `Boolean`, lub [daty](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   Typ konwersji z typu danych lub obiektu na typ pochodny  
  
 Zawężanie konwersji nie zawsze pomyślnie w czasie wykonywania i może się nie powieść lub pociągnąć za sobą utraty danych. Jeśli docelowy typ danych nie może odebrać wartość konwertowanej wystąpi błąd. Na przykład konwersja liczbowa może spowodować przepełnienie. Kompilator nie pozwala na niejawnie wykonywania konwersji zawężającej, chyba że [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia typ sprawdzania przełącznik `Off`.  
  
> [!NOTE]
>  Błąd zawężanie konwersji jest pomijane w przypadku konwersji z typu elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli for. Aby uzyskać dodatkowe informacje i przykłady, zobacz sekcję "Zawężanie konwersji" w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kiedy należy używać zawężanie konwersji  
 Za pomocą konwersji zawężającej wiadomo, że wartość źródła można przekonwertować na typ docelowy danych bez błędów i utraty danych. Na przykład, jeśli masz `String` czy znasz zawiera "wartość prawda" lub "False", można użyć `CBool` słowo kluczowe, aby przekonwertować go na `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Wyjątki podczas konwertowania  
 Rozszerzanie konwersji zawsze powiedzie się, nie zgłaszają wyjątki. Zawężanie konwersji, gdy się one zakończyć niepowodzeniem, throw najczęściej następujące wyjątki:  
  
-   <xref:System.InvalidCastException> — Jeśli zdefiniowano brak konwersji między tymi dwoma typami  
  
-   <xref:System.OverflowException> — (tylko w całkowitym typy) Jeśli skonwertowana wartość jest za duża dla typu docelowego  
  
 Jeśli definiuje klasę lub strukturę [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) jako operator konwersji na lub z tej klasy lub struktury, która `CType` może zgłosić wszelkie wyjątki, które uzna za stosowne. Ponadto, który `CType` może wywoływać funkcje języka Visual Basic lub [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody, które z kolei może wywoływać różnych wyjątków.  
  
## <a name="changes-during-reference-type-conversions"></a>Zmian podczas konwersji typu odwołania  
 Konwersja z *zawierają odwołania do typu* kopiuje tylko wskaźnik do wartości. Samą wartość nie jest kopiowany ani zmienione w dowolny sposób. Jedyną operacją, które można zmienić ma typ danych zmiennej zawierający wskaźnika. W poniższym przykładzie typ danych jest konwertowana z klasy pochodnej na jej klasa podstawowa, ale obie zmienne teraz wskaż obiekt jest bez zmian.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Konwertowanie między ciągami a innymi typami danych](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Porady: konwertowanie obiektu do innego typu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
