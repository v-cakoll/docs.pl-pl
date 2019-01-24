---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ffafff915af8a94e9bc135246064e4c049d41838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596465"
---
# <a name="isnot-operator-visual-basic"></a>IsNot — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. A `Boolean` wartość.  
  
 `object1`  
 Wymagana. Wszelkie `Object` zmiennej lub wyrażenia.  
  
 `object2`  
 Wymagana. Wszelkie `Object` zmiennej lub wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 `IsNot` Określa operator, jeśli dwa odwołania do obiektu odnoszą się do różnych obiektów. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `False`; Jeśli nie, `result` jest `True`.  
  
 `IsNot` jest to odwrotność `Is` operatora. Zaletą `IsNot` jest uniknięcie niewygodna składni `Not` i `Is`, który może być trudne do odczytania.  
  
 Możesz użyć `Is` i `IsNot` operatorów, aby przetestować obiekty z wczesnym wiązaniem i z późnym wiązaniem.  
  
> [!NOTE]
>  `IsNot` Operator nie może służyć do porównywania zwrócone w wyniku wyrażenia `TypeOf` operatora. Zamiast tego należy użyć `Not` i `Is` operatorów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu użyto obu `Is` operatora i `IsNot` operatora, aby osiągnąć ten sam porównania.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Instrukcje: Sprawdź, czy dwa obiekty są takie Same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
