---
title: IsTrue — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 1152f4b512a85ae183f8fc8d476b69685e2926ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966919"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue — Operator (Visual Basic)
Określa, czy wyrażenie jest `True`.  
  
 Nie można jawnie `IsTrue` wywołać w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z `OrElse` klauzul. W przypadku zdefiniowania klasy lub struktury, a następnie użycia zmiennej tego typu w `OrElse` klauzuli, należy zdefiniować `IsTrue` dla tej klasy lub struktury.  
  
 Kompilator traktuje `IsTrue` operatory i `IsFalse` jako pasującą *parę*. Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.  
  
## <a name="compiler-use-of-istrue"></a>Użycie kompilatora IsTrue  
 Po zdefiniowaniu klasy lub struktury można użyć zmiennej tego typu w `For` `If`instrukcji,, `Else If`, lub `While` w `When` klauzuli. W takim przypadku kompilator wymaga operatora, który konwertuje typ na `Boolean` wartość, aby umożliwić przetestowanie warunku. Wyszukuje odpowiedni operator w następującej kolejności:  
  
1. Rozszerzający Operator konwersji z klasy lub struktury do `Boolean`.  
  
2. Rozszerzający Operator konwersji z klasy lub struktury do `Boolean?`.  
  
3. `IsTrue` Operator klasy lub struktury.  
  
4. Zawężanie konwersji na `Boolean?` , która nie obejmuje konwersji z `Boolean` do `Boolean?`.  
  
5. Wąski Operator konwersji z klasy lub struktury do `Boolean`.  
  
 Jeśli nie zdefiniowano żadnej konwersji do `Boolean` `IsTrue` operatora OR, kompilator sygnalizuje błąd.  
  
> [!NOTE]
> Operator może być przeciążony, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury. `IsTrue` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje `IsFalse` operatorów i. `IsTrue`  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse, operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
