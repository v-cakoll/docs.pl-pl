---
title: Element <type1>„<typename>” musi implementować element „<methodname>” dla interfejsu „<interfacename>”
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 90d2b6d70390bfb732af4a5868c935de61d18f94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408502"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>Element \<type1>„\<typename>” musi implementować element „\<methodname>” dla interfejsu „\<interfacename>”
Klasa lub struktura oświadczenia do implementacji interfejsu, ale nie implementuje procedury zdefiniowanej przez interfejs. Każdy element członkowski interfejsu musi być zaimplementowany.  
  
 **Identyfikator błędu:** BC30149  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zadeklaruj procedurę o tej samej nazwie i podpisie, zgodnie z definicją w interfejsie. Pamiętaj, aby uwzględnić co najmniej `End Function` instrukcję or `End Sub` .  
  
2. Dodaj `Implements` klauzulę do końca `Function` `Sub` instrukcji or. Przykład:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Implements — Instrukcja](../statements/implements-statement.md)
- [Interfejsy](../../programming-guide/language-features/interfaces/index.md)
