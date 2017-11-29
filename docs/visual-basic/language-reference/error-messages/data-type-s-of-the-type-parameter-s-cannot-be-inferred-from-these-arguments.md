---
title: "Na podstawie tych argumentów nie można wywnioskować typów danych parametrów typu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b290c25286dce2236823919e8287db9abefc0dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
