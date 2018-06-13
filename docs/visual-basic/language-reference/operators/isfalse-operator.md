---
title: IsFalse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600050"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse — Operator (Visual Basic)
Określa, czy wyrażenie jest `False`.  
  
 Nie można wywołać `IsFalse` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `AndAlso` klauzul. Jeśli można zdefiniować klasy lub struktury, a następnie użyć zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.  
  
 Kompilator uwzględnia `IsFalse` i `IsTrue` operatorów jako *dopasowane pary*. Oznacza to, że jeśli jedna z nich zostanie zdefiniowana, należy także zdefiniować innego.  
  
> [!NOTE]
>  `IsFalse` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania podczas jej argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje konturu struktury, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
