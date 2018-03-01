---
title: "Decimal — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a>Decimal — Typ danych (Visual Basic)
Blokad podpisany 128-bitowego (16-bajtową) wartości reprezentujących skalowania zmiennej siły 10 numerów 96-bitową liczbę całkowitą (12-bajtowych). Czynnik skalowania określa liczbę cyfr z prawej strony punktu dziesiętnego; zakresy go z zakresu od 0 do 28. O skali 0 (bez miejsc dziesiętnych), największa możliwa wartość to +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28). 28 miejsc dziesiętnych największą wartość jest +/-7.9228162514264337593543950335 i najmniejszą wartość niezerową jest +/-0,0000000000000000000000000001 (+/-1E-28).  
  
## <a name="remarks"></a>Uwagi  
 `Decimal` — Typ danych zapewnia największą liczbę cyfr znaczących liczbą. Obsługuje maksymalnie 29 cyfr znaczących i może reprezentować wartości ponad 7.9228 x 10 ^ 28. Jest szczególnie przydatny w obliczeniach, takich jak finansowych, które wymagają dużą liczbę cyfr, ale nie może tolerować błędy zaokrąglania.  
  
 Wartość domyślna `Decimal` ma wartość 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Precyzja.** `Decimal`nie jest typem danych zmiennoprzecinkowych. `Decimal` Struktura zawiera wartość całkowitą binarnego, wraz z bitowego logowania i całkowitą skalowanie czynnik, który określa, jaka część wartość ułamek dziesiętny. W związku z tym `Decimal` liczby mają dokładniejsze reprezentacji w pamięci, niż typów zmiennoprzecinkowych (`Single` i `Double`).  
  
-   **Wydajność.** `Decimal` — Typ danych jest ładowane najwolniej wszystkie typy liczbowe. Należy porównać znaczenie dokładności względem wydajności przed wybraniem typu danych.  
  
-   **Rozszerzanie.** `Decimal` Rozszerzenie typu danych do `Single` lub `Double`. Oznacza to, że można przekonwertować `Decimal` jednej z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Końcowe zero.** Visual Basic nie przechowuje końcowe zero w `Decimal` literału. Jednak `Decimal` zmiennej zachowuje końcowe zera nabyte w praktyce. Ilustruje to poniższy przykład.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     Dane wyjściowe `MsgBox` w poprzednim przykładzie ma następującą składnię:  
  
     D1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4  
  
-   **Znaki typu.** Znak literalny typu dołączanie `D` do literału wymusza `Decimal` — typ danych. Dołączanie znak typu identyfikator `@` dla wszystkich identyfikatorów wymusza `Decimal`.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Decimal?displayProperty=nameWithType> struktury.  
  
## <a name="range"></a>Zakres  
 Konieczne może być `D` znak można przypisać duża wartość do typu `Decimal` zmiennej lub stałą. To wymaganie dotyczy, ponieważ kompilator interpretowana jako literału `Long` , chyba że znak literalny typu następuje literału, jak przedstawiono na poniższym przykładzie.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 Deklaracja `bigDec1` nie tworzy przepełnienie, ponieważ wartość przypisana do niego znajduje się w zakresie `Long`. `Long` Można przypisać wartości do `Decimal` zmiennej.  
  
 Deklaracja `bigDec2` generuje błąd przepełnienia, ponieważ wartość, która jest do niego przypisany jest za duża dla `Long`. Ponieważ literał liczbowy najpierw nie może być interpretowane jako `Long`, nie można przypisać do `Decimal` zmiennej.  
  
 Aby uzyskać `bigDec3`, znak literalny typu `D` rozwiązuje problem, powodując, że kompilator, aby zinterpretować jako literał `Decimal` zamiast jako `Long`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Single — typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Double — typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
