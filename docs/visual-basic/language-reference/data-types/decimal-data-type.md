---
title: Decimal — Typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: bab5a0bd7e0a85d550362bc3c1166566f6dcb81b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512769"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal — Typ danych (Visual Basic)

Przechowuje podpisane 128-bitowe (16-bajtowe) wartości reprezentujące liczby całkowite 96-bitowe (12-bajtowe) skalowane przez zmienną moc 10. Współczynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; dział IT mieści się w zakresie od 0 do 28. W przypadku skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28). W przypadku 28 miejsc dziesiętnych największą wartością jest +/-7.9228162514264337593543950335, a najmniejsza wartość niezerowa to +/-0,0000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>Uwagi

Typ `Decimal` danych zapewnia największą liczbę cyfr znaczących w liczbie. Obsługuje do 29 cyfr znaczących i może reprezentować wartości przekraczające 7,9228 x 10 ^ 28. Jest to szczególnie przydatne w przypadku obliczeń, takich jak finansowe, które wymagają dużej liczby cyfr, ale nie mogą tolerować błędów zaokrąglania.

Wartość `Decimal` domyślna to 0.

## <a name="programming-tips"></a>Porady dla programistów

- **Dokładne.** `Decimal`nie jest typem danych zmiennoprzecinkowych. `Decimal` Struktura zawiera binarną wartość całkowitą, łącznie z bitem znaku i czynnikiem skalowania liczby całkowitej, która określa, jaka część wartości jest ułamk dziesiętny. Z tego `Decimal` powodu liczby mają bardziej precyzyjną reprezentację w pamięci niż typy zmiennoprzecinkowe (`Single` i `Double`).

- **Wydajność.** Typ `Decimal` danych jest najwolniej ze wszystkich typów liczbowych. Przed wybraniem typu danych należy zaważyć znaczenie dokładności względem wydajności.

- **Rozszerzającą.** Typ danych poszerza do `Single` lub `Double`. `Decimal` Oznacza to, że można `Decimal` przekonwertować na jeden z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Końcowe zera.** Visual Basic nie przechowuje końcowych zer w `Decimal` literale. Jednak zmienna zachowuje `Decimal` obliczenia w sposób obliczeniowy. Ilustruje to poniższy przykład.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  Dane wyjściowe `MsgBox` w poprzednim przykładzie są następujące:

  ```
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Znaki typu.** Dołączanie znaku `D` typu literału do literału wymusza jego `Decimal` typ danych. Dołączanie znaku `@` typu identyfikatora do dowolnego identyfikatora zmusza go do `Decimal`.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> strukturą.

## <a name="range"></a>Zakres
 Może być konieczne użycie znaku typu `D` , aby przypisać dużą wartość `Decimal` do zmiennej lub stałej. To wymaganie wynika z faktu, że kompilator interpretuje literał jako `Long` , chyba że znak typu literału jest zgodny z literałem, jak pokazano w poniższym przykładzie.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

Deklaracja dla `bigDec1` nie produkuje przepełnienia, ponieważ przypisana do niej wartość znajduje się w zakresie dla `Long`. Wartość może być przypisana `Decimal` do zmiennej. `Long`

Deklaracja dla `bigDec2` generuje błąd przepełnienia, ponieważ przypisana do niego wartość jest za duża dla `Long`. Ponieważ literał liczbowy nie może być najpierw interpretowany jako `Long`, nie można go przypisać `Decimal` do zmiennej.

W `bigDec3`przypadku, znak `D` typu literału rozwiązuje problem, wymuszając kompilator, aby `Decimal` interpretował literał jako zamiast `Long`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Single, typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
