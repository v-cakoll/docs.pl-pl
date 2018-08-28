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
ms.openlocfilehash: 6578a410e389a313b0bad70f043691240e288887
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999711"
---
# <a name="numeric-data-types-visual-basic"></a>Numeric — Typ danych (Visual Basic)
Visual Basic dostarcza kilka *typy danych numerycznych* do obsługi liczb w różnych reprezentacji. *Całkowite* typy reprezentują tylko liczby całkowite (dodatnie, ujemne i zera), i *nonintegral* typy reprezentujące liczby zarówno liczba całkowita, jak i ułamkowe.  
  
 Aby uzyskać tabelę przedstawiającą porównanie side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Całkowite typy liczbowe  
 *Typy całkowite danych* te, które reprezentują tylko liczby bez części ułamkowej.  
  
 *Podpisany* integralnymi typami danych są [SByte — typ danych](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bitowa) [krótkiej — typ danych](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bitowy), [Integer — typ danych](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bitowa) i [ Long — typ danych](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bitowe). Jeśli zmienna przechowuje zawsze liczb całkowitych zamiast liczbami ułamkowymi, Zadeklaruj go jako jednego z tych typów.  
  
 *Niepodpisane* typów całkowitych są [Byte — typ danych](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bitowa) [ushort — typ danych](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bitowy), [uinteger — typ danych](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bitowa) i [ Ulong — typ danych](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bitowe). Jeśli zmienna zawiera dane binarne lub dane o charakterze nieznany, Zadeklaruj go jako jednego z tych typów.  
  
### <a name="performance"></a>Wydajność  
 Operacje arytmetyczne są szybsze działanie w przypadku typów całkowitych niż z innymi typami danych. Są one najszybszy z `Integer` i `UInteger` typy w języku Visual Basic.  
  
### <a name="large-integers"></a>Dużych liczb całkowitych  
 Jeśli potrzebujesz do przechowywania większa niż liczba całkowita `Integer` może zawierać danych typu, możesz użyć `Long` zamiast tego typu danych. `Long` Zmienne mogą zawierać liczb z-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807. Operacje dotyczące `Long` są nieco wolniej niż `Integer`.  
  
 Jeśli jeszcze większym wartości będą potrzebne, można użyć [typu danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Może zawierać liczb z-79,228,162,514,264,337,593,543,950,335 za pośrednictwem 79,228,162,514,264,337,593,543,950,335 w `Decimal` zmiennej, jeśli nie korzystają z dowolnego miejsca po przecinku. Jednak operacje `Decimal` liczby są znacznie wolniejsze niż z żadnym innym typem danych liczbowych.  
  
### <a name="small-integers"></a>Małe liczb całkowitych  
 Jeśli nie potrzebujesz pełnego zakresu `Integer` typu danych, można użyć `Short` typ danych, który może zawierać liczby całkowite od-32 768 za pośrednictwem 32 767 znaków. Dla najmniejszego zakres liczb całkowitych `SByte` — typ danych zawiera liczby całkowite od -128 do 127. Jeśli masz bardzo dużej liczby zmiennych, które pełnią małej liczby całkowite, środowisko uruchomieniowe języka wspólnego czasami mogą przechowywać swoje `Short` i `SByte` zmienne bardziej wydajnie, a następnie zapisz zużycie pamięci. Jednak operacje `Short` i `SByte` są nieco wolniej niż `Integer`.  
  
### <a name="unsigned-integers"></a>Liczb całkowitych bez znaku  
 Jeśli wiesz, że Twoja zmienna nigdy nie musi przechowywać wartość ujemną, możesz użyć *niepodpisanych typów*`Byte`, `UShort`, `UInteger`, i `ULong`. Każdy z tych typów danych może zawierać dodatnią liczbą całkowitą dwa razy większy zgodnie z odpowiadającymi mu dostawcami podpisany typ (`SByte`, `Short`, `Integer`, i `Long`). Pod względem wydajności każdy typ bez znaku jest dokładnie tak wydajna, jak jego odpowiedni typ ze znakiem. W szczególności `UInteger` udostępni `Integer` rozróżnienie jest najbardziej efektywne wszystkie typy podstawowe dane liczbowe.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral typy liczbowe  
 *Typy danych nonintegral* te, które reprezentują cyfr z liczbą całkowitą i części ułamkowych.  
  
 Typy danych liczbowych nonintegral `Decimal` (128-bitowego stały point), [jednego typu danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bitowych zmiennoprzecinkowych), i [typ danych Double](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bitowy zmiennoprzecinkowy punkt). Są one wszystko podpisane typów. Jeśli zmienna może zawierać ułamek, Zadeklaruj go jako jednego z tych typów.  
  
 `Decimal` nie jest typem danych zmiennopozycyjnych. `Decimal` numery mają wartość całkowitą binarne i współczynnik skalowania liczby całkowitej, która określa, jaka część wartości jest ułamek dziesiętny.  
  
 Możesz użyć `Decimal` zmienne dla wartości pieniężnych. Zaletą jest to precyzja wartości. `Double` — Typ danych jest szybsza i wymaga mniej pamięci, ale podlega błędów zaokrąglania. `Decimal` — Typ danych zachowuje pełną dokładności do 28 miejsc po przecinku.  
  
 Zmiennoprzecinkowe (`Single` i `Double`) liczby mają zakresy większych niż `Decimal` liczby, ale mogą podlegać błędów zaokrąglania. Typy zmiennoprzecinkowe obsługują mniej cyfr znaczących niż `Decimal` , ale może reprezentować wartości większe znaczenie.  
  
 Nonintegral wartości liczbowe mogą być wyrażone jako mmmEeee, w których jest mmm *mantysy* (cyfr znaczących) i jest See *wykładnik* (power 10). Najwyższej wartości dodatnich nonintegral typów są 7.9228162514264337593543950335E + 28, aby uzyskać `Decimal`, 3.4028235E + 38 dla `Single`i 1.79769313486231570E + 308 do `Double`.  
  
### <a name="performance"></a>Wydajność  
 `Double` jest najbardziej efektywne typy danych ułamkowych, ponieważ procesorów na platformach bieżącego wykonywania operacji zmiennoprzecinkowej w podwójnej precyzji. Jednak operacje `Double` nie są tak szybko, podobnie jak w przypadku typów całkowitych, takie jak `Integer`.  
  
### <a name="small-magnitudes"></a>Małe wielkości  
 W przypadku liczb o najniższej wartości możliwe (najbliżej 0) `Double` zmienne mogą, przechowywać numery będzie tak małej, jak - 4.94065645841246544E-324 dla wartości ujemnych i 4.94065645841246544E-324 dla wartości dodatnich.  
  
### <a name="small-fractional-numbers"></a>Małe liczb ułamkowych  
 Jeśli nie potrzebujesz pełnego zakresu `Double` typu danych, można użyć `Single` typ danych, który może zawierać liczb zmiennoprzecinkowych z - 3.4028235E + 38, za pośrednictwem 3.4028235E + 38. Najmniejsza wielkości dla `Single` zmienne są - 1, 401298E-45 dla wartości ujemnych i 1, 401298E-45 dla wartości dodatnich. W przypadku bardzo dużej liczby zmiennych, które pełnią small zmiennopozycyjnych środowiska uruchomieniowego języka wspólnego czasami mogą przechowywać swoje `Single` zmienne bardziej wydajnie, a następnie zapisz zużycie pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Różne typy danych](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
