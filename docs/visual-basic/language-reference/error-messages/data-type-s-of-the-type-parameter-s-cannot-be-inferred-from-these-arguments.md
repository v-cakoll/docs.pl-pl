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
ms.openlocfilehash: 68ed7541d76c1678f9f308ed2cda8afec1231a73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608722"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu
Nie można wywnioskować typów danych parametrów typu na podstawie tych argumentów. Określanie danych typów jawnie może rozwiązać ten problem.  
  
 Ten błąd występuje, gdy Rozpoznanie przeciążenia nie powiodło się. Jest wykonywane jako podrzędnego komunikat informujący o tym, dlaczego został wyeliminowany kandydat określonego przeciążenia. Komunikat o błędzie wyjaśniono, że kompilator nie mogą używać wnioskowania o typie można znaleźć typów danych parametrów typu.  
  
> [!NOTE]
>  Gdy określenie argumentów nie jest opcją (na przykład dla operatorów zapytań w wyrażeniach zapytań), bez drugie zdanie pojawi się komunikat o błędzie.  
  
 Poniższy przykład demonstruje ten błąd.  
  
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
  
-   Można określić typu danych dla parametru typu lub parametrów zamiast polegania na wnioskowanie o typie.  
  
## <a name="see-also"></a>Zobacz także
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Procedury ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
