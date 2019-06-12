---
title: <type1>'<typename>musi implementować<membername>'dla interfejsu'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 86b0d46e0e27b2fd8d1fccb37f4a3c45e95f5f63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792096"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > '\<typename >' musi implementować '\<membername >' dla interfejsu '\<interfacename >'
'\<typename >' musi implementować '\<membername >' dla interfejsu '\<interfacename >'. Implementowanie właściwości musi mieć dopasowania 'ReadOnly' / specyfikatorów 'WriteOnly'.  
  
 Klasa lub struktura oświadczeń zaimplementować interfejs, ale nie implementuje procedurę, właściwości lub zdarzenia, zdefiniowany przez interfejs. Należy zaimplementować każdego członka interfejsu.  
  
 **Identyfikator błędu:** BC30154  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zadeklaruj element członkowski o takiej samej nazwie i podpisie, zgodnie z definicją w interfejsie. Pamiętaj uwzględnić co najmniej `End Function`, `End Sub`, lub `End Property` instrukcji.  
  
2. Dodaj `Implements` klauzulę na końcu `Function`, `Sub`, `Property`, lub `Event` instrukcji. Na przykład:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Podczas implementowania właściwością, upewnij się, że `ReadOnly` lub `WriteOnly` jest używana w taki sam sposób jak w definicji interfejsu.  
  
4. Podczas implementowania właściwość, należy zadeklarować `Get` i `Set` procedur, zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
