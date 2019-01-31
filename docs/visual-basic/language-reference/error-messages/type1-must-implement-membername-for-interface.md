---
title: <type1>'<typename>' musi zaimplementować '<membername>' dla interfejsu '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: de7dd9026e08495941a89be0db11ad4c68d2a748
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264235"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > "\<typename >" musi implementować "\<membername >" dla interfejsu "\<interfacename >"
"\<typename >" musi implementować "\<membername >" dla interfejsu "\<interfacename >". Implementowanie właściwości musi mieć dopasowania "ReadOnly" / specyfikatorów "WriteOnly".  
  
 Klasa lub struktura oświadczeń zaimplementować interfejs, ale nie implementuje procedurę, właściwości lub zdarzenia, zdefiniowany przez interfejs. Należy zaimplementować każdego członka interfejsu.  
  
 **Identyfikator błędu:** BC30154  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zadeklaruj element członkowski o takiej samej nazwie i podpisie, zgodnie z definicją w interfejsie. Pamiętaj uwzględnić co najmniej `End Function`, `End Sub`, lub `End Property` instrukcji.  
  
2.  Dodaj `Implements` klauzulę na końcu `Function`, `Sub`, `Property`, lub `Event` instrukcji. Na przykład:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Podczas implementowania właściwością, upewnij się, że `ReadOnly` lub `WriteOnly` jest używana w taki sam sposób jak w definicji interfejsu.  
  
4.  Podczas implementowania właściwość, należy zadeklarować `Get` i `Set` procedur, zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
