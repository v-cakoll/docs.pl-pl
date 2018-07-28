---
title: Rozszerzanie i zwężanie konwersji (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: e574c20ec259953fea4b11d8f65e546373a4fe8c
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332577"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozszerzanie i zwężanie konwersji (Visual Basic)
Ważną kwestią za pomocą konwersji typu jest, czy wynik konwersji znajduje się w zakresie docelowego typu danych.  
  
 A *poszerzenie konwersji* zmienia wartość na typ danych, który można zezwolić na wszystkie możliwe wartości oryginalnych danych.  Konwersje rozszerzające zachować wartość źródła, ale można zmienić jej reprezentacji. Dzieje się tak w przypadku konwersji z typu całkowitego `Decimal`, lub z `Char` do `String`.  
  
 A *konwersja zawężająca* zmienia wartość na typ danych, który może nie posiadać pewnych możliwych wartości. Na przykład, wartość ułamkowa jest zaokrąglana przy jest konwertowany na typ całkowitoliczbowy i typ liczbowy, są konwertowane na `Boolean` jest ograniczona do jednej `True` lub `False`.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli przedstawiono standardowe poszerzenia konwersje.  
  
|Typ danych|Rozszerza się do typów danych <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Dowolny typ wyliczany ([wyliczenia](../../../../visual-basic/language-reference/statements/enum-statement.md))|Jego typ podstawowy dla typu całkowitego i dowolny typ, do której rozszerzenie podstawowego typu.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` Tablica|`Char` Tablica, `String`|  
|Dowolnego typu|[obiekt](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Dowolny typ pochodny|Podstawowa dowolnego typu, z którego pochodzi <sup>3</sup>.|  
|Dowolnego typu|Interfejs, który implementuje.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Typ danych lub typ obiektu.|  
  
 <sup>1</sup> zgodnie z definicją, co typ danych rozszerza się do samego siebie.  
  
 <sup>2</sup> konwersje z `Integer`, `UInteger`, `Long`, `ULong`, lub `Decimal` do `Single` lub `Double` może spowodować utratę dokładności, ale nigdy nie spowoduje utratę wielkości. W tym sensie nie wiążą się prawdopodobieństwo utraty informacji.  
  
 <sup>3</sup> mogą wydawać się Zaskakujące, że jest rozszerzanie konwersji z typu pochodnego do jednej z jej typów podstawowych. Uzasadnienie jest, że typ pochodny zawiera wszystkie elementy członkowskie w typie podstawowym, więc kwalifikuje się jako wystąpienie typu podstawowego. W przeciwnym kierunku typu podstawowego nie zawiera żadnych nowych elementów członkowskich zdefiniowanych przez typ pochodny.  
  
 Konwersje rozszerzające zawsze kończą się pomyślnie w czasie wykonywania i nigdy nie pociągnąć za sobą utratę danych. Zawsze wykonuj je w sposób niejawny, czy [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia typ sprawdzania przełącznik `On` lub `Off`.  
  
## <a name="narrowing-conversions"></a>Konwersje zawężające  
 Standardowe konwersje zawężające obejmują:  
  
-   Zwrotny instrukcjami konwersje rozszerzające w poprzednim tabeli (z tą różnicą, że każdy typ rozszerza się do samego siebie)  
  
-   Konwersje w dowolnym kierunku, między [logiczna](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) i dowolnego typu liczbowego  
  
-   Konwersje z dowolnego typu liczbowego na dowolny typ wyliczany (`Enum`)  
  
-   Konwersje w dowolnym kierunku, między [ciąg](../../../../visual-basic/language-reference/data-types/string-data-type.md) i dowolnego typu liczbowego `Boolean`, lub [daty](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   Konwersje z typu danych lub obiekt typu do typu, który pochodzi z niego  
  
 Konwersje zawężające nie zawsze sukces w czasie wykonywania i może zakończyć się niepowodzeniem lub pociągnąć za sobą utratę danych. Błąd występuje, jeśli docelowy typ danych nie może odbierać konwertowana wartość. Na przykład konwersja liczbowa może spowodować przepełnienie. Kompilator nie pozwalają na wykonywać konwersje zawężające niejawnie, chyba że [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia typ sprawdzania przełącznik `Off`.  
  
> [!NOTE]
>  Błąd konwersji zawężających jest pomijana dla konwersji z elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli. Aby uzyskać więcej informacji i przykładów, zobacz sekcję "Konwersje zawężające" w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kiedy należy używać zwężanie konwersji  
 Konwersja zawężająca jest używany, gdy wiesz, że można przekonwertować daną wartość źródła do docelowego typu danych bez utraty danych lub błąd. Na przykład, jeśli masz `String` czy wiesz, zawiera "wartość prawda" lub "False", możesz użyć `CBool` słowo kluczowe, aby przekonwertować go pod kątem `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Wyjątki podczas konwertowania  
 Ponieważ konwersje rozszerzające zawsze powiedzie się, nie zgłaszają wyjątków. Konwersje zawężające, gdy zakończą się niepowodzeniem, najczęściej wyrzucić następujące:  
  
-   <xref:System.InvalidCastException> — Jeśli konwersja nie jest zdefiniowana między dwoma typami  
  
-   <xref:System.OverflowException> — (tylko typy całkowite) Jeśli przekonwertowana wartość jest zbyt duża dla typu docelowego  
  
 Jeśli zdefiniowano klasy lub struktury [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) ma pełnić rolę operatora konwersji do i z tej klasy lub struktury, która `CType` można zgłoszenie każdego wyjątku, które uzna za stosowne. Ponadto, który `CType` może wywoływać funkcje języka Visual Basic lub [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody, które z kolei może wywoływać różnych wyjątków.  
  
## <a name="changes-during-reference-type-conversions"></a>Zmiany w czasie konwersji typu odwołania  
 Konwersja z *odwołania do typu* kopiuje tylko wskaźnik do wartości. Sama wartość nie jest kopiowany ani zmieniać w jakikolwiek sposób. Jedyną czynnością, którą mogą zmieniać to typ danych zmiennej Przytrzymanie wskaźnika myszy. W poniższym przykładzie typ danych jest konwertowany z klasy pochodnej do swojej klasy bazowej, ale obiekt, który obu zmiennych wskazują teraz pozostaje niezmieniony.  
  
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
 [Porady: konwertowanie obiektu na inny typ w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
