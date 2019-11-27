---
title: Operator IsNot
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336075"
---
# <a name="isnot-operator-visual-basic"></a>IsNot — Operator (Visual Basic)

Porównuje dwie zmienne odwołań do obiektów.

## <a name="syntax"></a>Składnia

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Części
 Wymagane `result`. Wartość `Boolean`.

 Wymagane `object1`. Dowolna `Object` zmienna lub wyrażenie.

 Wymagane `object2`. Dowolna `Object` zmienna lub wyrażenie.

## <a name="remarks"></a>Uwagi
 Operator `IsNot` określa, czy dwa odwołania do obiektów odwołują się do różnych obiektów. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `object2` oba odnoszą się do tego samego wystąpienia obiektu, `result` jest `False`; Jeśli tak nie jest, `result` jest `True`.

 `IsNot` jest przeciwieństwem operatora `Is`. Zaletą `IsNot` jest możliwość uniknięcia składni niewygodna z `Not` i `Is`, co może być trudne do odczytania.

 Można użyć operatorów `Is` i `IsNot` do testowania zarówno obiektów wczesnych, jak i z późnym wiązaniem.

## <a name="example"></a>Przykład
 Poniższy przykład kodu używa operatora `Is` i operatora `IsNot` do wykonania tego samego porównania.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Zobacz także

- [Is, operator](is-operator.md)
- [TypeOf, operator](typeof-operator.md)
- [Pierwszeństwo operatorów w Visual Basic](operator-precedence.md)
- [Instrukcje: testowanie, czy dwa obiekty są takie same](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
