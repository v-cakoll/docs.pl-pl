---
title: "Parametrów typu nie można używać jako kwalifikatorów"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametrów typu nie można używać jako kwalifikatorów
Element programowania jest kwalifikowany za pomocą kwalifikacji ciąg, który zawiera parametr typu.  
  
 Parametr typu reprezentuje typ, który ma zostać podane w przypadku typu ogólnego jest tworzony. Ten element nie reprezentuje określonego typu zdefiniowane. Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.  
  
 Poniższe instrukcje może spowodować wygenerowanie tego błędu.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **Identyfikator błędu:** BC32098  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń parametr typu z ciągu kwalifikacji lub Zamień zdefiniowanego typu.  
  
2.  Jeśli musisz użyć skonstruowanego typu można znaleźć elementu programistycznego jest kwalifikowana, należy użyć dodatkowe logice programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
