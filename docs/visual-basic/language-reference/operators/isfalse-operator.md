---
title: Operator IsFalse
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349530"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse — Operator (Visual Basic)
Określa, czy wyrażenie jest `False`.  
  
 Nie można jawnie wywołać `IsFalse` w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z klauzul `AndAlso`. Jeśli zdefiniujesz klasę lub strukturę, a następnie użyjesz zmiennej tego typu w klauzuli `AndAlso`, musisz zdefiniować `IsFalse` dla tej klasy lub struktury.  
  
 Kompilator traktuje operatory `IsFalse` i `IsTrue` jako *pasującą parę*. Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.  
  
> [!NOTE]
> Operator `IsFalse` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować swoje zachowanie, gdy jego operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje dla operatorów `IsFalse` i `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
