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
ms.openlocfilehash: 4d530a8c1f85d2f0045184c05df63849047a8204
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971773"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal — Typ danych (Visual Basic)
Przechowuje podpisany 128-bitowego (16-bajtową) wartości reprezentujących numery 96-bitową liczbę całkowitą z (12-bajtową) skalowania przez zmienną potęgą liczby 10. Czynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; waha się od 0 do 28. O skali 0 (bez miejsc dziesiętnych) największa możliwa wartość to +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28). 28 miejsc dziesiętnych największa wartość jest +/-7.9228162514264337593543950335 i najmniejszą wartość różną od zera jest +/-0,0000000000000000000000000001 (+/-1E-28).  
  
## <a name="remarks"></a>Uwagi  
 `Decimal` — Typ danych zapewnia największą liczbę cyfr znaczących liczbą. Obsługuje więcej niż 29 cyfr znaczących i może reprezentować wartości przekraczające 7.9228 x 10 ^ 28. Jest szczególnie przydatny w obliczeniach, takich jak finansowych, które wymagają dużej liczby cyfr, ale nie tolerują błędy zaokrągleń.  
  
 Wartość domyślna `Decimal` wynosi 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Dokładność.** `Decimal` nie jest typem danych zmiennopozycyjnych. `Decimal` Struktury przechowuje wartość całkowitą binarne, wraz z bitem znaku i współczynnik, która określa, jaka część wartości jest ułamek dziesiętny skalowania liczby całkowitej. W związku z tym `Decimal` liczby mają bardziej precyzyjne reprezentacji w pamięci, niż typów zmiennoprzecinkowych (`Single` i `Double`).  
  
- **Wydajność.** `Decimal` Typ danych jest najwolniejsze wszystkich typów liczbowych. Należy porównać znaczenie dokładności względem wydajności przed wybraniem typu danych.  
  
- **Rozszerzanie.** `Decimal` — Typ danych rozszerza się na `Single` lub `Double`. Oznacza to, że możesz przekonwertować `Decimal` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Końcowe zera.** Visual Basic nie przechowuje zera końcowe w `Decimal` literału. Jednak `Decimal` zmienna zachowuje dowolne zera końcowe, które zostały nabyte w praktyce. Ilustruje to poniższy przykład.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     Dane wyjściowe `MsgBox` w powyższym przykładzie jest następująca:  
  
     d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4  
  
- **Znaki typu.** Dołączanie znaku typu literał `D` do literału wymusza `Decimal` typu danych. Dołączanie znaku typu identyfikator `@` do jakiegokolwiek identyfikatora wymusza `Decimal`.  
  
- **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> struktury.  
  
## <a name="range"></a>Zakres  
 Może być konieczne użycie `D` wpisz znak duża wartość, aby przypisać `Decimal` zmienną lub stałą. Jest to wymaganie, ponieważ kompilator interpretuje słowa kluczowe literału jako `Long` chyba, że znak literalny typu następuje literału, co ilustruje poniższy przykład.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 Deklaracja `bigDec1` nie generuje przepełnienie, ponieważ wartość, która jest przypisana do niego znajduje się w zakresie dla `Long`. `Long` Można przypisać wartości do `Decimal` zmiennej.  
  
 Deklaracja `bigDec2` generuje błąd przepełnienia, ponieważ wartość, która jest przypisana do niego jest za duży dla `Long`. Ponieważ literału liczbowego najpierw nie mogą być interpretowane jako `Long`, nie można przypisać do `Decimal` zmiennej.  
  
 Aby uzyskać `bigDec3`, znak literalny typu `D` rozwiązuje problem, wymuszając na kompilatorze interpretowanie literału jako `Decimal` zamiast jako `Long`.  
  
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
