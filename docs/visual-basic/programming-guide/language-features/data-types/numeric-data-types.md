---
title: Numeric — Typ danych (Visual Basic)
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
ms.openlocfilehash: 8fa88172c9914a071e1b24e959c9030e6d219a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="numeric-data-types-visual-basic"></a>Numeric — Typ danych (Visual Basic)
Visual Basic dostarcza kilku *numeryczne typy danych* do obsługi liczby w różnych reprezentacji. *Całkowite* typy reprezentują tylko liczby całkowite (dodatnie, ujemne i zero), a *nonintegral* typy reprezentujące liczby z liczbą całkowitą i ułamkowych części.  
  
 Aby uzyskać tabelę przedstawiającą porównanie side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="integral-numeric-types"></a>Numeryczne typy całkowite  
 *Typy całkowite danych* są tymi, które reprezentują tylko cyfry bez części ułamkowej.  
  
 *Podpisany* są typy całkowite danych [SByte — typ danych](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bitów) [krótkich — typ danych](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bitowy), [Integer — typ danych](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bitowy) i [ Long — typ danych](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bitowe). Jeśli zmienna zawsze przechowuje liczb całkowitych, a nie z liczbami ułamkowymi, należy zadeklarować go jako jednego z tych typów.  
  
 *Niepodpisane* są typy całkowite [Byte — typ danych](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bitów) [ushort — typ danych](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bitowy), [uinteger — typ danych](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bitowy) i [ Ulong — typ danych](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bitowe). Jeśli zmienna zawiera dane binarne lub dane o charakterze nieznany, Zadeklaruj ją jako jeden z tych typów.  
  
### <a name="performance"></a>Wydajność  
 Operacje arytmetyczne są szybsze z typów całkowitych od innych typów danych. Są one najszybszym z `Integer` i `UInteger` typów w języku Visual Basic.  
  
### <a name="large-integers"></a>Dużej liczby całkowite  
 Jeśli potrzebujesz do przechowywania liczbą całkowitą większą niż `Integer` może zawierać danych typu, możesz użyć `Long` zamiast tego typu danych. `Long` zmienne może zawierać cyfry od-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807. Operacje z `Long` są nieco wolniej niż `Integer`.  
  
 Jeśli potrzebujesz jeszcze większym wartości, możesz użyć [typu danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Może zawierać cyfry od-79,228,162,514,264,337,593,543,950,335 za pośrednictwem 79,228,162,514,264,337,593,543,950,335 w `Decimal` zmiennej, jeśli nie używasz żadnych miejsc dziesiętnych. Jednak operacje przy użyciu `Decimal` liczby są znacznie wolniejsze niż w przypadku każdego typu danych liczbowych.  
  
### <a name="small-integers"></a>Małej liczby całkowite  
 Jeśli nie potrzebujesz pełnego zakresu `Integer` typu danych, można użyć `Short` typ danych, który może zawierać liczby całkowite od-32 768 do 32 767. Aby uzyskać najmniejszą liczbą całkowitą `SByte` — typ danych przechowuje liczby całkowite od -128 do 127. Jeśli masz dużą liczbę zmiennych zawierających małej liczby całkowite, czasem może przechowywać środowisko uruchomieniowe języka wspólnego programu `Short` i `SByte` zmienne wydajniej, a następnie zapisz zużycie pamięci. Jednak operacje przy użyciu `Short` i `SByte` są nieco wolniej niż `Integer`.  
  
### <a name="unsigned-integers"></a>Liczb całkowitych bez znaku  
 Jeśli wiesz, że do zmiennej nigdy nie należy do przechowywania liczbą ujemną, możesz użyć *niepodpisanych typów*`Byte`, `UShort`, `UInteger`, i `ULong`. Każdy z tych typów danych może zawierać dodatnią liczbą całkowitą dwa razy większy jako odpowiednie podpisany typ (`SByte`, `Short`, `Integer`, i `Long`). Pod względem wydajności dokładnie tak wydajna, jak jego odpowiedniego typu ze znakiem jest każdego typu bez znaku. W szczególności `UInteger` udostępnia `Integer` rozróżnienie jest najbardziej wydajnym wszystkie typy podstawowe dane liczbowe.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral typy liczbowe  
 *Typy danych nonintegral* to takie, które reprezentują liczb z liczbą całkowitą i ułamkowych części.  
  
 Typy danych numerycznych nonintegral są `Decimal` (128-bitowego stałego punktu), [jednego typu danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bitowych zmiennoprzecinkowych), i [Double — typ danych](../../../../visual-basic/language-reference/data-types/double-data-type.md) (punkt przestawne 64-bitowe). Są one typy wszystko podpisane. Jeśli zmienna może zawierać ułamek, Zadeklaruj ją jako jeden z tych typów.  
  
 `Decimal` nie jest typem danych zmiennoprzecinkowych. `Decimal` liczby mają wartość całkowitą binarne i czynnik skalowania liczba całkowita, która określa, jaka część wartość jest ułamek dziesiętny.  
  
 Można użyć `Decimal` zmienne dla wartości pieniędzy. Zaletą jest dokładność wartości. `Double` — Typ danych jest szybsze i wymaga mniej pamięci, ale podlega błędów zaokrąglania. `Decimal` — Typ danych zachowuje pełną dokładność do 28 miejsc po przecinku.  
  
 Zmiennoprzecinkowe (`Single` i `Double`) liczby mają zakresy większych niż `Decimal` numery, ale mogą podlegać błędów zaokrąglania. Typy zmiennoprzecinkowe obsługują mniejszą liczbę cyfr znaczących niż `Decimal` , ale może reprezentować wartości większe znaczenie.  
  
 Nonintegral wartości liczbowe może zostać wyrażona jako mmmEeee, w których jest mmm *mantysa* (cyfr znaczących) i jest See *wykładnik* (power 10). Najwyższej wartości dodatnie nonintegral typów są 7.9228162514264337593543950335E + 28 dla `Decimal`, 3.4028235E + 38 dla `Single`i 1.79769313486231570E + 308 do `Double`.  
  
### <a name="performance"></a>Wydajność  
 `Double` jest najbardziej wydajnym typy danych ułamkowych, ponieważ procesorów na platformach bieżącego wykonywania operacji zmiennoprzecinkowych w podwójnej precyzji. Jednak operacje przy użyciu `Double` nie są tak szybko, jak w przypadku typów całkowitych, takich jak `Integer`.  
  
### <a name="small-magnitudes"></a>Małe wielkości  
 W przypadku numerów o najniższej wartości możliwe (znajdujący się najbliżej 0) `Double` zmienne można, przytrzymaj numery będzie jak - 4.94065645841246544E-324 dla wartości ujemnych i 4.94065645841246544E-324 dla wartości dodatnie.  
  
### <a name="small-fractional-numbers"></a>Mała liczb ułamkowych  
 Jeśli nie potrzebujesz pełnego zakresu `Double` typu danych, można użyć `Single` typ danych, który może zawierać liczb zmiennoprzecinkowych od - 3.4028235E + 38 za pośrednictwem 3.4028235E + 38. Najmniejsza wielkości dla `Single` zmienne są - 1, 401298E-45 dla wartości ujemnych i 1, 401298E-45 dla wartości dodatnie. Jeśli masz dużą liczbę zmiennych, mające mały liczb zmiennoprzecinkowych, czasem może przechowywać środowisko uruchomieniowe języka wspólnego programu `Single` zmienne wydajniej, a następnie zapisz zużycie pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Różne typy danych](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
