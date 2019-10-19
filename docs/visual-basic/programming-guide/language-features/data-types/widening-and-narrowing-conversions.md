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
ms.openlocfilehash: d1822afc4b10a725e13c1469a068c30813d3a2d3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582733"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozszerzanie i zwężanie konwersji (Visual Basic)
Ważnym zagadnieniem dotyczącym konwersji typów jest to, czy wynik konwersji należy do zakresu docelowego typu danych.  
  
 *Konwersja rozszerzająca* zmienia wartość na typ danych, który może zezwalać na dowolną możliwą wartość oryginalnych danych.  Konwersje rozszerzające zachowują wartość źródłową, ale mogą zmieniać jej reprezentację. Dzieje się tak w przypadku konwersji z typu całkowitego na `Decimal` lub z `Char` do `String`.  
  
 *Konwersja zawężania* zmienia wartość na typ danych, który może nie być w stanie przechowywać niektórych możliwych wartości. Na przykład wartość ułamkowa jest zaokrąglana, gdy jest konwertowana na typ całkowity, a typ liczbowy konwertowany na `Boolean` jest zredukowany do `True` lub `False`.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli przedstawiono standardowe konwersje rozszerzające.  
  
|Typ danych|Rozszerzanie do typów danych <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bajc](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Wybierak](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single` `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Całkowitą](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger —](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Długo](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Dokładności](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Wiersz](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Dowolny typ wyliczeniowy ([enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Jego bazowego typu całkowitego i dowolnego typu, do którego rozszerzany jest typ podstawowy.|  
|[Delikatn](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|Tablica `Char`|`Char` Array, `String`|  
|Dowolny typ|[Stream](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Dowolny typ pochodny|Każdy typ podstawowy, z którego pochodzi <sup>3</sup>.|  
|Dowolny typ|Każdy interfejs, który implementuje.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Typ danych lub typ obiektu.|  
  
 <sup>1</sup> według definicji każdy typ danych jest poszerzany do samego siebie.  
  
 <sup>2</sup> konwersje z `Integer`, `UInteger`, `Long`, `ULong` lub `Decimal` do `Single` lub `Double` mogą spowodować utratę precyzji, ale nigdy nie ma utraty wielkości. W tym sensie nie wiążą się z utratą informacji.  
  
 <sup>3</sup> może wydawać się zaskakujące, że konwersja z typu pochodnego do jednego z jego typów podstawowych jest poszerzana. Uzasadnienie polega na tym, że typ pochodny zawiera wszystkie elementy członkowskie typu podstawowego, więc jest on uznawany za wystąpienie typu podstawowego. W przeciwnym kierunku typ podstawowy nie zawiera żadnych nowych elementów członkowskich zdefiniowanych przez typ pochodny.  
  
 Rozszerzanie konwersji zawsze powiedzie się w czasie wykonywania i nigdy nie powiąże się z utratą danych. Można je zawsze wykonać niejawnie, niezależnie od tego, czy [opcja Strict Option](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia przełącznik sprawdzania typu na `On` lub `Off`.  
  
## <a name="narrowing-conversions"></a>Konwersje zawężające  
 Standardowe konwersje wąskie obejmują następujące elementy:  
  
- Odwrotne instrukcje konwersji rozszerzających w powyższej tabeli (z tą różnicą, że każdy typ rozszerza się do samego siebie)  
  
- Konwersje w obu kierunkach między [wartością logiczną](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) i dowolnym typem liczbowym  
  
- Konwersje z dowolnego typu liczbowego na dowolny typ wyliczeniowy (`Enum`)  
  
- Konwersje w dowolnym kierunku między [ciągiem](../../../../visual-basic/language-reference/data-types/string-data-type.md) i dowolnym typem liczbowym, `Boolean` lub [datą](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
- Konwersje z typu danych lub typu obiektu na typ pochodzący od niego  
  
 Konwersje wąskie nie zawsze kończą się powodzeniem w czasie wykonywania i mogą kończyć się niepowodzeniem lub spowodować utratę danych. Błąd występuje, jeśli docelowy typ danych nie może otrzymać konwertowanej wartości. Na przykład konwersja numeryczna może spowodować przepełnienie. Kompilator nie pozwala na wykonywanie konwersji zawężających niejawnie, chyba że [instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawia przełącznik sprawdzania typu na `Off`.  
  
> [!NOTE]
> Zawężanie — błąd konwersji jest pomijany dla konwersji z elementów w kolekcji `For Each…Next` do zmiennej kontroli pętli. Aby uzyskać więcej informacji i przykładów, zobacz sekcję "Konwersje wąskie" w sekcji [for each... Next — instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kiedy należy używać konwersji zawężania  
 Możesz użyć konwersji wąskiej, gdy wiesz, że wartość źródłowa może zostać przekonwertowana na typ danych docelowych bez błędu lub utraty danych. Jeśli na przykład masz `String` o wartości "true" lub "false", możesz użyć słowa kluczowego `CBool`, aby przekonwertować go na `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Wyjątki podczas konwersji  
 Ponieważ konwersje rozszerzające zawsze powiodło się, nie generują wyjątków. Konwersje wąskie, gdy nie powiodą się, najczęściej generują następujące wyjątki:  
  
- <xref:System.InvalidCastException> — Jeśli konwersja między dwoma typami nie jest zdefiniowana  
  
- <xref:System.OverflowException> — (tylko typy całkowite), jeśli przekonwertowana wartość jest zbyt duża dla typu docelowego  
  
 Jeśli klasa lub struktura definiuje [funkcję CType](../../../../visual-basic/language-reference/functions/ctype-function.md) , która służy jako operator konwersji do lub z tej klasy lub struktury, która `CType` może zgłosić każdy wyjątek, który jest uważany za właściwy. Ponadto `CType` mogą wywoływać funkcje Visual Basic lub .NET Framework metody, które z kolei mogą zgłosić wiele wyjątków.  
  
## <a name="changes-during-reference-type-conversions"></a>Zmiany podczas konwersji typów odwołań  
 Konwersja z *typu referencyjnego* kopiuje tylko wskaźnik do wartości. Sama wartość nie jest kopiowana ani zmieniana w żaden sposób. Jedyną czynnością, którą można zmienić, jest typ danych zmiennej przechowującej wskaźnik. W poniższym przykładzie typ danych jest konwertowany z klasy pochodnej do jej klasy bazowej, ale obiekt, który od razu wskazuje, jest niezmieniony.  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Konwertowanie między ciągami a innymi typami danych](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Instrukcje: konwertowanie obiektu na inny typ w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
