---
title: Element <type1>„<typename>” musi implementować element „<membername>” dla interfejsu „<interfacename>”
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696897"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > "\<typename >" musi implementować element "\<membername >" dla interfejsu "\<interfacename >"
element "\<typename >" musi implementować element "\<membername >" dla interfejsu "\<interfacename >". Implementacja właściwości musi mieć pasujące specyfikatory "ReadOnly"/"WriteOnly".  
  
 Klasa lub struktura oświadczenia do implementacji interfejsu, ale nie implementuje procedury, właściwości lub zdarzenia zdefiniowanego przez interfejs. Każdy element członkowski interfejsu musi być zaimplementowany.  
  
 **Identyfikator błędu:** BC30154  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zadeklaruj element członkowski o takiej samej nazwie i podpisie, jak zdefiniowano w interfejsie. Pamiętaj, aby uwzględnić co najmniej `End Function`, `End Sub` lub `End Property` instrukcji.  
  
2. Dodaj klauzulę `Implements` na końcu `Function`, `Sub`, `Property` lub `Event` instrukcji. Na przykład:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Podczas implementowania właściwości upewnij się, że `ReadOnly` lub `WriteOnly` są używane w taki sam sposób jak w definicji interfejsu.  
  
4. Podczas implementowania właściwości należy zadeklarować procedury `Get` i `Set`, zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
