---
title: Decimal, typ danych
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
ms.openlocfilehash: 690c8061b6df1115aa24668520170b44edfa8287
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415650"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal — Typ danych (Visual Basic)

Przechowuje podpisane 128-bitowe (16-bajtowe) wartości reprezentujące liczby całkowite 96-bitowe (12-bajtowe) skalowane przez zmienną moc 10. Współczynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; dział IT mieści się w zakresie od 0 do 28. W przypadku skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28). W przypadku 28 miejsc dziesiętnych największą wartością jest +/-7.9228162514264337593543950335, a najmniejsza wartość niezerowa to +/-0,0000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>Uwagi

`Decimal`Typ danych zapewnia największą liczbę cyfr znaczących w liczbie. Obsługuje do 29 cyfr znaczących i może reprezentować wartości przekraczające 7,9228 x 10 ^ 28. Jest to szczególnie przydatne w przypadku obliczeń, takich jak finansowe, które wymagają dużej liczby cyfr, ale nie mogą tolerować błędów zaokrąglania.

Wartość domyślna `Decimal` to 0.

## <a name="programming-tips"></a>Porady dla programistów

- **Dokładne.** `Decimal`nie jest typem danych zmiennoprzecinkowych. `Decimal`Struktura zawiera binarną wartość całkowitą, łącznie z bitem znaku i czynnikiem skalowania liczby całkowitej, która określa, jaka część wartości jest ułamk dziesiętny. Z tego powodu `Decimal` liczby mają bardziej precyzyjną reprezentację w pamięci niż typy zmiennoprzecinkowe ( `Single` i `Double` ).

- **Skuteczności.** `Decimal`Typ danych jest najwolniej ze wszystkich typów liczbowych. Przed wybraniem typu danych należy zaważyć znaczenie dokładności względem wydajności.

- **Rozszerzającą.** `Decimal`Typ danych poszerza do `Single` lub `Double` . Oznacza to, że można przekonwertować `Decimal` na jeden z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Końcowe zera.** Visual Basic nie przechowuje końcowych zer w `Decimal` literale. Jednak `Decimal` zmienna zachowuje obliczenia w sposób obliczeniowy. Ilustruje to poniższy przykład.

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

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Znaki typu.** Dołączanie znaku typu literału `D` do literału wymusza jego `Decimal` Typ danych. Dołączanie znaku typu identyfikatora `@` do dowolnego identyfikatora zmusza go do `Decimal` .

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> strukturą.

## <a name="range"></a>Zakres

 Może być konieczne użycie `D` znaku typu, aby przypisać dużą wartość do `Decimal` zmiennej lub stałej. To wymaganie wynika z faktu, że kompilator interpretuje literał jako `Long` , chyba że znak typu literału jest zgodny z literałem, jak pokazano w poniższym przykładzie.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

Deklaracja dla `bigDec1` nie produkuje przepełnienia, ponieważ przypisana do niej wartość znajduje się w zakresie dla `Long` . `Long`Wartość może być przypisana do `Decimal` zmiennej.

Deklaracja dla `bigDec2` generuje błąd przepełnienia, ponieważ przypisana do niego wartość jest za duża dla `Long` . Ponieważ literał liczbowy nie może być najpierw interpretowany jako `Long` , nie można go przypisać do `Decimal` zmiennej.

W przypadku `bigDec3` , znak typu literału `D` rozwiązuje problem, wymuszając kompilator, aby interpretował literał jako `Decimal` zamiast `Long` .

## <a name="see-also"></a>Zobacz też

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Single, typ danych](single-data-type.md)
- [Double, typ danych](double-data-type.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
