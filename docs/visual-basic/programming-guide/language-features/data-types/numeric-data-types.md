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
ms.openlocfilehash: 72cdca295e209935687f67ad290e816775d9fe13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393679"
---
# <a name="numeric-data-types-visual-basic"></a>Numeric — Typ danych (Visual Basic)
Visual Basic dostarcza kilka *typów danych liczbowych* do obsługi liczb w różnych reprezentacji. Typy *całkowite* reprezentują tylko liczby całkowite (dodatnie, ujemne i zero), a typy *niecałkowite* reprezentują liczby z liczbami całkowitymi i częściowymi.  
  
 Aby uzyskać tabelę zawierającą porównanie równoległe typów danych Visual Basic, zobacz [typy danych](../../../language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Całkowite typy liczbowe  
 *Całkowite typy danych* to te, które reprezentują tylko liczby bez części ułamkowych.  
  
 Typy danych całkowitych ze *znakiem* są [typu danych](../../../language-reference/data-types/sbyte-data-type.md) (8-bitowy), [Krótki typ danych](../../../language-reference/data-types/short-data-type.md) (16-bitowy), [Typ danych Integer](../../../language-reference/data-types/integer-data-type.md) (32-bitowy) i [długi typ danych](../../../language-reference/data-types/long-data-type.md) (64-bitowy). Jeśli zmienna zawsze przechowuje liczby całkowite zamiast liczb ułamkowych, należy zadeklarować ją jako jeden z tych typów.  
  
 Typy całkowite *bez znaku* są [typu danych bajtowych](../../../language-reference/data-types/byte-data-type.md) (8-bitowe), [UShort Data Type](../../../language-reference/data-types/ushort-data-type.md) (16-bitowy), [Typ danych UInteger —](../../../language-reference/data-types/uinteger-data-type.md) (32-bitowy) i [ULONG](../../../language-reference/data-types/ulong-data-type.md) (64-bitowy). Jeśli zmienna zawiera dane binarne lub dane nieznanego charakteru, deklaruj ją jako jeden z tych typów.  
  
### <a name="performance"></a>Wydajność  
 Operacje arytmetyczne są szybsze przy użyciu typów całkowitych niż z innymi typami danych. Są one najszybciej zgodne z `Integer` `UInteger` typami i w Visual Basic.  
  
### <a name="large-integers"></a>Duże liczby całkowite  
 Jeśli musisz pomieścić liczbę całkowitą większą niż `Integer` Typ danych, można użyć `Long` zamiast tego typu danych. `Long`zmienne mogą zawierać cyfry od-zakresu od do 9 223 372 036 854 775 807. Operacje z programem `Long` są nieco wolniejsze niż w przypadku programu `Integer` .  
  
 Jeśli potrzebujesz jeszcze większych wartości, możesz użyć [typu danych dziesiętnych](../../../language-reference/data-types/decimal-data-type.md). Można przechowywać liczby z-79228162514264337593543950335 do 79228162514264337593543950335 w zmiennej, `Decimal` Jeśli nie używasz żadnych miejsc dziesiętnych. Jednak operacje z `Decimal` liczbami są znacznie wolniejsze niż w przypadku dowolnego innego typu danych liczbowych.  
  
### <a name="small-integers"></a>Małe liczby całkowite  
 Jeśli nie potrzebujesz pełnego zakresu `Integer` typu danych, możesz użyć `Short` typu danych, który może zawierać liczby całkowite od-32 768 do 32 767. Dla najmniejszego zakresu liczb całkowitych `SByte` Typ danych przechowuje liczby całkowite od-128 do 127. W przypadku bardzo dużej liczby zmiennych, które przechowują małe liczby całkowite, środowisko uruchomieniowe języka wspólnego może czasami przechowywać `Short` zmienne i `SByte` zwiększyć wydajność pamięci. Jednak operacje z `Short` i `SByte` są nieco wolniejsze niż w przypadku programu `Integer` .  
  
### <a name="unsigned-integers"></a>Liczby całkowite bez znaku  
 Jeśli wiesz, że zmienna nigdy nie musi zawierać liczby ujemnej, możesz użyć *typów bez znaku*,, `Byte` `UShort` `UInteger` i `ULong` . Każdy z tych typów danych może pomieścić dodatnią liczbę całkowitą dwa razy, tak jak w przypadku odpowiedniego podpisanego typu ( `SByte` , `Short` , `Integer` i `Long` ). Pod względem wydajności każdy typ bez znaku jest dokładnie tak wydajny, jak odpowiadający mu typ podpisywany. W szczególności `UInteger` udziały z `Integer` rozróżnieniem są najbardziej wydajne dla wszystkich podstawowych liczbowych typów danych.  
  
## <a name="nonintegral-numeric-types"></a>Niecałkowite typy liczbowe  
 *Niecałkowitymi typami danych* są te, które reprezentują liczby zarówno liczby całkowite, jak i części ułamkowe.  
  
 Niecałkowite typy danych liczbowych to `Decimal` (128-bitowy stały punkt), [pojedynczy typ danych](../../../language-reference/data-types/single-data-type.md) (32-bitowy zmiennoprzecinkowy) i [podwójny typ danych](../../../language-reference/data-types/double-data-type.md) (64-bit zmiennoprzecinkowy). Są to wszystkie typy podpisane. Jeśli zmienna może zawierać ułamek, deklaruj ją jako jeden z tych typów.  
  
 `Decimal`nie jest typem danych zmiennoprzecinkowych. `Decimal`liczby mają wartość binarną integer i współczynnik skalowania liczby całkowitej, który określa, jaka część wartości jest ułamk dziesiętny.  
  
 Można używać `Decimal` zmiennych dla wartości pieniężnych. Zaletą jest precyzja wartości. `Double`Typ danych jest szybszy i wymaga mniejszej ilości pamięci, ale podlega zaokrąglaniu błędów. `Decimal`Typ danych zachowuje pełną dokładność do 28 miejsc dziesiętnych.  
  
 Liczby zmiennoprzecinkowe ( `Single` i `Double` ) mają większe zakresy niż `Decimal` liczby, ale mogą być objęte zaokrąglaniem błędów. Typy zmiennoprzecinkowe obsługują mniej znaczące cyfry, `Decimal` ale mogą reprezentować wartości o większej wielkości.  
  
 Niecałkowite wartości liczbowe można wyrazić jako mmmEeee, w którym MMM to *mantysy* (znaczące cyfry), a Eee to *wykładnik* (potęga 10). Najwyższe wartości dodatnie typów niecałkowitych są 7.9228162514264337593543950335 E + 28 dla `Decimal` , 3.4028235 e + 38 dla `Single` i 1.79769313486231570 e + 308 dla `Double` .  
  
### <a name="performance"></a>Wydajność  
 `Double`jest najbardziej wydajne dla ułamkowych typów danych, ponieważ procesory na bieżących platformach wykonują operacje zmiennoprzecinkowe w podwójnej precyzji. Jednak operacje z `Double` nie są tak szybkie jak w przypadku typów całkowitych, takich jak `Integer` .  
  
### <a name="small-magnitudes"></a>Małe rozmiary  
 W przypadku liczb o najmniejszej możliwej wielkości (najbliżej 0) `Double` zmienne mogą przechowywać cyfry jako małe 4.94065645841246544 e-324 dla wartości ujemnych i 4.94065645841246544 e-324 dla wartości dodatnich.  
  
### <a name="small-fractional-numbers"></a>Małe liczby ułamkowe  
 Jeśli nie potrzebujesz pełnego zakresu `Double` typu danych, możesz użyć `Single` typu danych, który może zawierać liczby zmiennoprzecinkowe z-3.4028235 e + 38 za pośrednictwem 3.4028235 e + 38. Najmniejszy rozmiar dla `Single` zmiennych to-1.401298 e-45 dla wartości ujemnych i 1.401298 e-45 dla wartości dodatnich. W przypadku bardzo dużej liczby zmiennych, które przechowują małe liczby zmiennoprzecinkowe, środowisko uruchomieniowe języka wspólnego może czasami przechowywać `Single` zmienne bardziej wydajnie i zaoszczędzić użycie pamięci.  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych podstawowych](elementary-data-types.md)
- [Znakowe typy danych](character-data-types.md)
- [Różne typy danych](miscellaneous-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
