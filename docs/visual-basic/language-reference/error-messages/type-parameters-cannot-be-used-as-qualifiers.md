---
title: Parametrów typu nie można używać jako kwalifikatorów
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595147"
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
