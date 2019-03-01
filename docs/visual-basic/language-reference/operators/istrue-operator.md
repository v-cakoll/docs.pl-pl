---
title: IsTrue — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: b2ec1a20e815ad38c2fdd984b9f9c35247dae81a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971315"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue — Operator (Visual Basic)
Określa, czy wyrażenie jest `True`.  
  
 Nie można wywołać `IsTrue` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `OrElse` klauzul. Jeśli zdefiniowano klasy lub struktury, a następnie użyć zmiennej tego typu w `OrElse` klauzuli, należy zdefiniować `IsTrue` dla tej klasy lub struktury.  
  
 Kompilator traktuje `IsTrue` i `IsFalse` operatorów jako *dopasowane pary*. Oznacza to, że jeśli zdefiniujesz jednego z nich, musisz również zdefiniować innego.  
  
## <a name="compiler-use-of-istrue"></a>Używanie kompilatora IsTrue  
 Po zdefiniowaniu klasy lub struktury, można użyć zmiennej tego typu w `For`, `If`, `Else If`, lub `While` instrukcji lub `When` klauzuli. Jeśli to zrobisz, kompilator wymaga operatora, który konwertuje danego typu w `Boolean` wartość, aby ją przetestować warunku. Wyszukuje odpowiedniego operatora w następującej kolejności:  
  
1.  Operatora konwersji rozszerzającej od klasy lub struktury do `Boolean`.  
  
2.  Operatora konwersji rozszerzającej od klasy lub struktury do `Boolean?`.  
  
3.  `IsTrue` Operator dla swojej klasy lub struktury.  
  
4.  Konwersja zawężająca do `Boolean?` nie wymaga konwersji `Boolean` do `Boolean?`.  
  
5.  Operatora konwersji zawężającej od klasy lub struktury do `Boolean`.  
  
 Jeśli nie zdefiniowano żadnych konwersji na `Boolean` lub `IsTrue` operatora, kompilator sygnalizuje błąd.  
  
> [!NOTE]
>  `IsTrue` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia zarys to struktura, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz także
- [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse, operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
