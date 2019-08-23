---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966936"
---
# <a name="isnot-operator-visual-basic"></a>IsNot — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. `Boolean` Wartość.  
  
 `object1`  
 Wymagana. Dowolna `Object` zmienna lub wyrażenie.  
  
 `object2`  
 Wymagane. Dowolna `Object` zmienna lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Operator `IsNot` określa, czy dwa odwołania do obiektów odwołują się do różnych obiektów. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `False` `result` `result` `True`oba odnoszą się do dokładnie tego samego wystąpienia obiektu, to; jeśli nie, to. `object2`  
  
 `IsNot`jest przeciwieństwem `Is` operatora. Zaletą `IsNot` jest to, że można uniknąć niewygodna składni z `Not` i `Is`, co może być trudne do odczytania.  
  
 Operatory `Is` i`IsNot` służą do testowania zarówno obiektów wczesnych, jak i z późnym wiązaniem.  
  
> [!NOTE]
> Nie można użyć `TypeOf` operatoradoporównaniawyrażeńzwracanych`IsNot` z operatora. Zamiast tego należy użyć `Not` operatorów i. `Is`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa `Is` operatora `IsNot` i operatora, aby wykonać to samo porównanie.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Zobacz także

- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Instrukcje: Sprawdź, czy dwa obiekty są takie same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
