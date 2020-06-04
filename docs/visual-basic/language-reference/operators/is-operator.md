---
title: Is, operator
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 3cc0ae5f04358fbe6b2aabc50498f39ca7225164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370807"
---
# <a name="is-operator-visual-basic"></a>Is — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolna `Boolean` wartość.  
  
 `object1`  
 Wymagany. Dowolna `Object` nazwa.  
  
 `object2`  
 Wymagany. Dowolna `Object` nazwa.  
  
## <a name="remarks"></a>Uwagi  
 `Is`Operator określa, czy dwa odwołania do obiektów odwołują się do tego samego obiektu. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `object2` oba odnoszą się do dokładnie tego samego wystąpienia obiektu, `result` to `True` ; Jeśli nie, `result` to `False` .  
  
 `Is`można go również użyć ze `TypeOf` słowem kluczowym, aby utworzyć `TypeOf` wyrażenie... `Is` , które sprawdza, czy zmienna obiektu jest zgodna z typem danych.  
  
> [!NOTE]
> `Is`Słowo kluczowe jest również używane w [SELECT... Case — instrukcja](../statements/select-case-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Is` operatora do porównywania par odwołań do obiektów. Wyniki są przypisane do `Boolean` wartości reprezentującej, czy dwa obiekty są identyczne.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak pokazano w powyższym przykładzie, można użyć `Is` operatora do przetestowania zarówno obiektów wczesnych, jak i późnych powiązań.  
  
## <a name="see-also"></a>Zobacz też

- [TypeOf — Operator](typeof-operator.md)
- [IsNot, operator](isnot-operator.md)
- [Operatory porównania w Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
