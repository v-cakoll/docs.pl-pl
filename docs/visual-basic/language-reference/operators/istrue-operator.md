---
title: "IsTrue — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0d261186ce68f06cec95251e815248a189f6da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="istrue-operator-visual-basic"></a>IsTrue — Operator (Visual Basic)
Określa, czy wyrażenie jest `True`.  
  
 Nie można wywołać `IsTrue` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `OrElse` klauzul. Jeśli można zdefiniować klasy lub struktury, a następnie użyć zmiennej tego typu w `OrElse` klauzuli, należy zdefiniować `IsTrue` dla tej klasy lub struktury.  
  
 Kompilator uwzględnia `IsTrue` i `IsFalse` operatorów jako *dopasowane pary*. Oznacza to, że jeśli jedna z nich zostanie zdefiniowana, należy także zdefiniować innego.  
  
## <a name="compiler-use-of-istrue"></a>Użycie kompilatora IsTrue  
 Po zdefiniowaniu klasy lub struktury, można użyć zmiennej tego typu w `For`, `If`, `Else``If`, lub `While` instrukcji lub `When` klauzuli. Jeśli to zrobisz, kompilator wymaga operatora, który konwertuje danego typu w `Boolean` wartość, aby było sprawdzić warunku. Wyszukuje odpowiedni operator w następującej kolejności:  
  
1.  Rozszerzającą operatora konwersji z klasy lub struktury, `Boolean`.  
  
2.  Rozszerzającą operatora konwersji z klasy lub struktury, `Boolean?`.  
  
3.  `IsTrue` Operator na klasy lub struktury.  
  
4.  Do konwersji zawężającej `Boolean?` nie wymaga konwersji `Boolean` do `Boolean?`.  
  
5.  Operator konwersji zawężającej od klasy lub struktury, `Boolean`.  
  
 Jeśli nie zdefiniowano żadnej konwersji do `Boolean` lub `IsTrue` operatora, kompilator sygnały wystąpił błąd.  
  
> [!NOTE]
>  `IsTrue` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania podczas jej argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje konturu struktury, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [IsFalse — Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Porady: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [OrElse — Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
