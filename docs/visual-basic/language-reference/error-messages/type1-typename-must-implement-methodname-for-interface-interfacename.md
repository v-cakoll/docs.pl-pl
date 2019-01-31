---
title: <type1>'<typename>' musi zaimplementować '<methodname>' dla interfejsu '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c5dd7c6889a3fb5344142ee9914f98e8922d748b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264440"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 > "\<typename >" musi implementować "\<methodname >" dla interfejsu "\<interfacename >"
Klasa lub struktura oświadczeń zaimplementować interfejs, ale nie implementuje określonymi przez interfejs. Należy zaimplementować każdego członka interfejsu.  
  
 **Identyfikator błędu:** BC30149  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zadeklaruj procedury o tej samej nazwie i podpisie, zgodnie z definicją w interfejsie. Pamiętaj uwzględnić co najmniej `End Function` lub `End Sub` instrukcji.  
  
2.  Dodaj `Implements` klauzulę na końcu `Function` lub `Sub` instrukcji. Na przykład:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
