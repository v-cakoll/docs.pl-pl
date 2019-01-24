---
title: IsFalse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: ec8d7bcd2f4ca3fb1c74f4edcf6ec8af78fd144d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740439"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse — Operator (Visual Basic)
Określa, czy wyrażenie jest `False`.  
  
 Nie można wywołać `IsFalse` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `AndAlso` klauzul. Jeśli zdefiniowano klasy lub struktury, a następnie użyć zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.  
  
 Kompilator traktuje `IsFalse` i `IsTrue` operatorów jako *dopasowane pary*. Oznacza to, że jeśli zdefiniujesz jednego z nich, musisz również zdefiniować innego.  
  
> [!NOTE]
>  `IsFalse` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia zarys to struktura, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
