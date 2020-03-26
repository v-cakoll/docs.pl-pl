---
title: Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 1660971e2a1a11d7a2d14f222cd149edf4aa4c7b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249516"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym

Zmienna zadeklarowana jako typ wartości nullable została `Nothing` porównana `IsNot` z wyrażeniem innym niż operator.

**Identyfikator błędu:** Bc32128

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Aby porównać typ nullable do `Nothing` wyrażenia `IsNot` innego niż `GetType` przy użyciu operatora, wywołać metodę na typ nullable i porównać wynik do wyrażenia, jak pokazano w poniższym przykładzie.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Zobacz też

- [Typy o wartości zerowalnej](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
