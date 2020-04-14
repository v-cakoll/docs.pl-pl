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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243326"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal — Typ danych (Visual Basic)

Posiada podpisane wartości całkowite 128-bitowe (16-bajtowe) reprezentujące 96-bitowe (12-bajtowe) liczby całkowite skalowane o zmienną moc 10. Współczynnik skalowania określa liczbę cyfr po prawej stronie przecinka dziesiętnego; waha się od 0 do 28. Przy skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79,228,162,514,264,337,593,1543 950 335 (+/-7,922816251426437593543950335E+28). Z miejscami po przecinku 28, największa wartość to +/-7.92281625251426437593543950335, a najmniejsza wartość niezerowa to +/-0.000000000000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>Uwagi

Typ `Decimal` danych zapewnia największą liczbę cyfr znaczących dla liczby. Obsługuje do 29 cyfr znaczących i może reprezentować wartości przekraczające 7,9228 x 10^28. Jest to szczególnie odpowiednie dla obliczeń, takich jak finansowe, które wymagają dużej liczby cyfr, ale nie tolerują błędów zaokrąglania.

Wartość domyślna `Decimal` to 0.

## <a name="programming-tips"></a>Porady dla programistów

- **Precyzji.** `Decimal`nie jest typem danych zmiennoprzecinkowych. Struktura `Decimal` zawiera binarną wartość całkowitą, wraz z bitem znaku i współczynnik skalowania liczby całkowitej, który określa, jaka część wartości jest ułamkiem dziesiętnym. Z tego `Decimal` powodu liczby mają bardziej precyzyjną reprezentację w`Single` `Double`pamięci niż typy zmiennoprzecinkowe ( i ).

- **Wydajności.** Typ `Decimal` danych jest najwolniejszy ze wszystkich typów liczbowych. Przed wybraniem typu danych należy rozważyć znaczenie precyzji w stosunku do wydajności.

- **Poszerzenie.** Typ `Decimal` danych rozszerza `Single` się `Double`do lub . Oznacza to, `Decimal` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.

- **Końcowe zera.** Visual Basic nie przechowuje końcowych `Decimal` zer w literału. Jednak zmienna `Decimal` zachowuje wszystkie końcowe zera nabyte obliczeniowo. Ilustruje to poniższy przykład.

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

- **Wpisz znaki.** Dołączenie znaku literału `D` do literału wymusza go do `Decimal` typu danych. Dołączenie znaku `@` typu identyfikatora do dowolnego identyfikatora wymusza jego `Decimal`

- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.Decimal?displayProperty=nameWithType> jest strukturą.

## <a name="range"></a>Zakres

 Może być konieczne `D` użycie znaku typu, aby `Decimal` przypisać dużą wartość do zmiennej lub stałej. To wymaganie jest, ponieważ kompilator `Long` interpretuje literału, chyba że znak typu literału następuje literał, jak pokazano w poniższym przykładzie.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

Deklaracja `bigDec1` dla nie powoduje przepełnienia, ponieważ wartość, która jest przypisana `Long`do niego mieści się w zakresie . Wartość `Long` można przypisać do `Decimal` zmiennej.

Deklaracja `bigDec2` dla generuje błąd przepełnienia, ponieważ wartość, która jest `Long`przypisana do niego jest zbyt duża dla . Ponieważ literał numeryczny nie może być najpierw `Long`interpretowany jako , nie `Decimal` można go przypisać do zmiennej.

Dla `bigDec3`, literał `D` typu znak rozwiązuje problem, zmuszając kompilator do `Decimal` interpretacji literału jako litera zamiast jako `Long`.

## <a name="see-also"></a>Zobacz też

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Single, typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
