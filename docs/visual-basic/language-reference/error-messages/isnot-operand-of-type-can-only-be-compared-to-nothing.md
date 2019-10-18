---
title: Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 06dc6f1532fecefba4e507bd0cc24aadc936d137
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524372"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym

Zmienna zadeklarowana jako Nullable została porównana z wyrażeniem innym niż `Nothing` przy użyciu operatora `IsNot`.

**Identyfikator błędu:** BC32128

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Aby porównać typ dopuszczający wartość null z wyrażeniem innym niż `Nothing` przy użyciu operatora `IsNot`, wywołaj metodę `GetType` dla typu dopuszczającego wartość null i porównaj wynik z wyrażeniem, jak pokazano w poniższym przykładzie.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Zobacz także

- [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
