---
title: Parametrów typu nie można używać jako kwalifikatorów
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 8ee0fd5822c22da090aa0abee679e2f68e0fc1d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659716"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametrów typu nie można używać jako kwalifikatorów
Elementu programistycznego kwalifikuje się ciągiem kwalifikacji, który zawiera parametr typu.  
  
 Parametr typu reprezentuje typ, która jest przekazywana, gdy typ ogólny jest skonstruowany. Go nie reprezentuje określonego typu zdefiniowane. Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.  
  
 Poniższe instrukcje może wygenerować tego błędu.  
  
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
  
2.  Jeśli musisz użyć skonstruowanego typu można zlokalizować elementu programistycznego, jest kwalifikowana, należy użyć dodatkowej logiki programu.  
  
## <a name="see-also"></a>Zobacz także
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
