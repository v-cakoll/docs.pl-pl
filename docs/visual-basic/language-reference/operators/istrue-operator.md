---
title: Operator IsTrue
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 4b863eed8406a10b9a44d7139f8659ac5cb758ad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349515"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue — Operator (Visual Basic)
Określa, czy wyrażenie jest `True`.  
  
 Nie można jawnie wywołać `IsTrue` w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z klauzul `OrElse`. Jeśli zdefiniujesz klasę lub strukturę, a następnie użyjesz zmiennej tego typu w klauzuli `OrElse`, musisz zdefiniować `IsTrue` dla tej klasy lub struktury.  
  
 Kompilator traktuje operatory `IsTrue` i `IsFalse` jako *pasującą parę*. Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.  
  
## <a name="compiler-use-of-istrue"></a>Użycie kompilatora IsTrue  
 Po zdefiniowaniu klasy lub struktury można użyć zmiennej tego typu w instrukcji `For`, `If`, `Else If`lub `While` lub w klauzuli `When`. W takim przypadku kompilator wymaga operatora, który konwertuje typ na wartość `Boolean`, aby umożliwić przetestowanie warunku. Wyszukuje odpowiedni operator w następującej kolejności:  
  
1. Poszerzenie operatora konwersji z klasy lub struktury do `Boolean`.  
  
2. Poszerzenie operatora konwersji z klasy lub struktury do `Boolean?`.  
  
3. Operator `IsTrue` w klasie lub strukturze.  
  
4. Zawężanie konwersji do `Boolean?`, która nie obejmuje konwersji z `Boolean` do `Boolean?`.  
  
5. Wąski Operator konwersji z klasy lub struktury do `Boolean`.  
  
 Jeśli nie zdefiniowano żadnej konwersji do `Boolean` lub operatora `IsTrue`, kompilator sygnalizuje błąd.  
  
> [!NOTE]
> Operator `IsTrue` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować swoje zachowanie, gdy jego operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje dla operatorów `IsFalse` i `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse, operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
