---
title: Nie można wywnioskować typu elementu „<variablename>”, ponieważ granice pętli i zmienna step nie mogą zostać poszerzone do tego samego typu
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512708"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Nie można wywnioskować typu "\<VariableName >", ponieważ granice pętli i zmienna kroku nie są rozszerzane do tego samego typu

Zapisano `For...Next` pętlę, w której kompilator nie może wywnioskować typu danych dla zmiennej kontroli pętli, ponieważ spełnione są następujące warunki:

- Typ danych zmiennej sterującej pętli nie jest określony z `As` klauzulą.

- Granice pętli i zmienna kroku zawierają co najmniej dwa typy danych.

- Między typami danych nie istnieje żadna konwersja standardowa.

 W związku z tym kompilator nie może wywnioskować typu danych zmiennej sterującej pętli.

 W poniższym przykładzie zmienna kroku jest znakiem, a granice pętli są liczbami całkowitymi. Ponieważ nie istnieje standardowa konwersja między znakami i liczbami całkowitymi, ten błąd jest zgłaszany.

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**Identyfikator błędu:** BC30982

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- W razie potrzeby zmień typy granic pętli i zmiennej krokowej, tak aby co najmniej jedna z nich została poszerzona. W poprzednim przykładzie Zmień typ `stepVar` na. `Integer`

  ```vb
  Dim stepVar = 1
  ```

  —lub—

  ```vb
  Dim stepVar As Integer = 1
  ```

- Użyj funkcji jawnej konwersji, aby przekonwertować granice pętli i zmienną krokową na odpowiednie typy. W poprzednim przykładzie Zastosuj `Val` funkcję do. `stepVar`

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
