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
ms.openlocfilehash: 6f84df5c9388220e5ca817d95362753df0920534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586815"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu
Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu. Określanie danych typów jawnie może rozwiązać ten problem.  
  
 Ten błąd występuje, gdy Rozpoznanie przeciążenia nie powiodło się. Nastąpi to jako podrzędny komunikat informujący o tym, dlaczego określonego przeciążenie kandydujące został wyeliminowany. Komunikat o błędzie wyjaśniono, że kompilator nie mogą używać wnioskowanie o typie można znaleźć typów danych parametrów typu.  
  
> [!NOTE]
>  Podczas określania argumentów nie jest opcją (na przykład dla operatorów zapytań w wyrażeniach zapytań), zostanie wyświetlony komunikat o błędzie bez drugie zdanie.  
  
 Poniższy kod przedstawia błędu.  
  
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
  
-   Można określić typ dla parametru typu lub parametrów zamiast polegania na wnioskowanie o typie danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Procedury ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
