---
title: Typy danych liczbowych
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346309"
---
# <a name="numeric-data-types-visual-basic"></a>Numeric — Typ danych (Visual Basic)
Visual Basic dostarcza kilka *typów danych liczbowych* do obsługi liczb w różnych reprezentacji. Typy *całkowite* reprezentują tylko liczby całkowite (dodatnie, ujemne i zero), a typy *niecałkowite* reprezentują liczby z liczbami całkowitymi i częściowymi.  
  
 Aby uzyskać tabelę zawierającą porównanie równoległe typów danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Całkowite typy liczbowe  
 *Całkowite typy danych* to te, które reprezentują tylko liczby bez części ułamkowych.  
  
 Typy danych całkowitych ze *znakiem* są [typu danych](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bitowy), [Krótki typ danych](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bitowy), [Typ danych Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bitowy) i [długi typ danych](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bitowy). Jeśli zmienna zawsze przechowuje liczby całkowite zamiast liczb ułamkowych, należy zadeklarować ją jako jeden z tych typów.  
  
 Typy całkowite *bez znaku* są [typu danych bajtowych](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bitowe), [UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bitowy), [Typ danych UInteger —](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bitowy) i [ULONG](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bitowy). Jeśli zmienna zawiera dane binarne lub dane nieznanego charakteru, deklaruj ją jako jeden z tych typów.  
  
### <a name="performance"></a>Wydajność  
 Operacje arytmetyczne są szybsze przy użyciu typów całkowitych niż z innymi typami danych. Są najszybciej z `Integer` i `UInteger` typów w Visual Basic.  
  
### <a name="large-integers"></a>Duże liczby całkowite  
 Jeśli musisz pomieścić liczbę całkowitą większą niż `Integer` typ danych, możesz użyć `Long` typu danych. zmienne `Long` mogą zawierać cyfry od-zakresu od do 9 223 372 036 854 775 807. Operacje o `Long` są nieco wolniejsze niż `Integer`.  
  
 Jeśli potrzebujesz jeszcze większych wartości, możesz użyć [typu danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Liczby z-79228162514264337593543950335 do 79228162514264337593543950335 można przechowywać w zmiennej `Decimal`, jeśli nie używasz żadnych miejsc dziesiętnych. Jednak operacje o liczbie `Decimal` są znacznie wolniejsze niż w przypadku dowolnego innego typu danych liczbowych.  
  
### <a name="small-integers"></a>Małe liczby całkowite  
 Jeśli nie potrzebujesz pełnego zakresu typu danych `Integer`, możesz użyć typu danych `Short`, który może zawierać liczby całkowite od-32 768 do 32 767. Dla najmniejszego zakresu liczb całkowitych typ danych `SByte` przechowuje liczby całkowite z zakresu od-128 do 127. W przypadku bardzo dużej liczby zmiennych, które przechowują małe liczby całkowite, środowisko uruchomieniowe języka wspólnego może czasami przechowywać `Short` i `SByte` zmienne bardziej wydajnie i zaoszczędzić użycie pamięci. Operacje z `Short` i `SByte` są jednak nieco wolniejsze niż w przypadku `Integer`.  
  
### <a name="unsigned-integers"></a>Liczby całkowite bez znaku  
 Jeśli wiesz, że zmienna nigdy nie musi zawierać liczby ujemnej, możesz użyć *typów bez znaku*`Byte`, `UShort`, `UInteger`i `ULong`. Każdy z tych typów danych może pomieścić dodatnią liczbę całkowitą dwa razy, jak jest to odpowiedni typ podpisany (`SByte`, `Short`, `Integer`i `Long`). Pod względem wydajności każdy typ bez znaku jest dokładnie tak wydajny, jak odpowiadający mu typ podpisywany. W szczególności `UInteger` udziały z `Integer` rozróżnienia są najbardziej wydajne dla wszystkich podstawowych liczbowych typów danych.  
  
## <a name="nonintegral-numeric-types"></a>Niecałkowite typy liczbowe  
 *Niecałkowitymi typami danych* są te, które reprezentują liczby zarówno liczby całkowite, jak i części ułamkowe.  
  
 Niecałkowitymi typami danych liczbowych są `Decimal` (128-bitowy stały punkt), [pojedynczy typ danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bitowy zmiennoprzecinkowy) i [podwójny typ danych](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit zmiennoprzecinkowy). Są to wszystkie typy podpisane. Jeśli zmienna może zawierać ułamek, deklaruj ją jako jeden z tych typów.  
  
 `Decimal` nie jest typem danych zmiennoprzecinkowych. liczby `Decimal` mają wartość binarną integer i współczynnik skalowania liczby całkowitej, która określa, jaka część wartości jest ułamkiem dziesiętnym.  
  
 W wartościach pieniężnych można używać zmiennych `Decimal`. Zaletą jest precyzja wartości. `Double` typ danych jest szybszy i wymaga mniejszej ilości pamięci, ale podlega zaokrąglaniu błędów. `Decimal` typ danych zachowuje pełną dokładność do 28 miejsc dziesiętnych.  
  
 Liczby zmiennoprzecinkowe (`Single` i `Double`) mają większe zakresy niż numery `Decimal`, ale mogą być objęte zaokrąglaniem błędów. Typy zmiennoprzecinkowe obsługują mniej znaczące cyfry niż `Decimal`, ale mogą reprezentować wartości większej wielkości.  
  
 Niecałkowite wartości liczbowe można wyrazić jako mmmEeee, w którym MMM to *mantysy* (znaczące cyfry), a Eee to *wykładnik* (potęga 10). Najwyższe wartości dodatnie typów niecałkowitych są 7.9228162514264337593543950335 E + 28 dla `Decimal`, 3.4028235 E + 38 dla `Single`i 1.79769313486231570 E + 308 dla `Double`.  
  
### <a name="performance"></a>Wydajność  
 `Double` to najbardziej wydajne wartości ułamkowe, ponieważ procesory na bieżących platformach wykonują operacje zmiennoprzecinkowe w podwójnej precyzji. Jednak operacje z `Double` nie są tak szybkie jak w przypadku typów całkowitych, takich jak `Integer`.  
  
### <a name="small-magnitudes"></a>Małe rozmiary  
 W przypadku liczb o najmniejszej możliwej wielkości (najbliżej 0) zmienne `Double` mogą przechowywać liczby jako małe 4.94065645841246544 E-324 dla wartości ujemnych i 4.94065645841246544 E-324 dla wartości dodatnich.  
  
### <a name="small-fractional-numbers"></a>Małe liczby ułamkowe  
 Jeśli nie potrzebujesz pełnego zakresu typu danych `Double`, możesz użyć typu danych `Single`, który może zawierać liczby zmiennoprzecinkowe z-3.4028235 E + 38 za pośrednictwem 3.4028235 E + 38. Najmniejsze rozmiary zmiennych `Single` są 1.401298 E-45 dla wartości ujemnych i 1.401298 E-45 dla wartości dodatnich. W przypadku bardzo dużej liczby zmiennych, które przechowują małe liczby zmiennoprzecinkowe, środowisko uruchomieniowe języka wspólnego może czasami przechowywać zmienne `Single` efektywniej i zaoszczędzić użycie pamięci.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Różne typy danych](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
