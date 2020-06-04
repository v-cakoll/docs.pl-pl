---
title: Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: b278dcc10a8a4e9e67aacdb16dca2588d2ebd0f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409790"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu

Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu. Jawne określenie typów danych może naprawić ten błąd.

Ten błąd występuje, gdy Rozpoznanie przeciążenia nie powiodło się. Występuje jako komunikat podrzędny informujący o tym, dlaczego określony kandydat przeciążenia został wyeliminowany. W komunikacie o błędzie wyjaśniono, że kompilator nie może użyć wnioskowania typu w celu znalezienia typów danych dla parametrów typu.

> [!NOTE]
> Gdy określenie argumentów nie jest opcją (na przykład w przypadku operatorów zapytań w wyrażeniach zapytań), komunikat o błędzie jest wyświetlany bez drugiego zdania.

Poniższy kod ilustruje błąd.

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

**Identyfikator błędu:** BC36647 i BC36644

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Możesz określić typ danych dla parametru lub parametrów typu, zamiast polegać na wnioskach o typie.

## <a name="see-also"></a>Zobacz też

- [Swobodna konwersja delegatów](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Procedury ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Konwersje plików w Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
