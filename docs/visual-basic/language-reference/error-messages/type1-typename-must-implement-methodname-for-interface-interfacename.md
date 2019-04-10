---
title: <type1>"<typename>musi implementować<methodname>"dla interfejsu"<interfacename>"
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304912"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 > "\<typename >" musi implementować "\<methodname >" dla interfejsu "\<interfacename >"
Klasa lub struktura oświadczeń zaimplementować interfejs, ale nie implementuje określonymi przez interfejs. Należy zaimplementować każdego członka interfejsu.  
  
 **Identyfikator błędu:** BC30149  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zadeklaruj procedury o tej samej nazwie i podpisie, zgodnie z definicją w interfejsie. Pamiętaj uwzględnić co najmniej `End Function` lub `End Sub` instrukcji.  
  
2. Dodaj `Implements` klauzulę na końcu `Function` lub `Sub` instrukcji. Na przykład:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Implements — Instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
