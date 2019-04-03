---
title: Element „<membername>” jest niejednoznaczny w dziedziczonych interfejsach „<interfacename1>” i „<interfacename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 4415608bcfca63b43b3d9ebf17ce622ccd418775
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820860"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a>"\<membername >" jest niejednoznaczny w dziedziczonych interfejsach\<interfacename1 > "i"\<interfacename2 > "
Interfejs dziedziczy dwóch lub więcej elementów członkowskich o takiej samej nazwie z wielu interfejsów.  
  
 **Identyfikator błędu:** BC30685  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Rzutuj wartość interfejs podstawowy, który chcesz użyć. na przykład:  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
