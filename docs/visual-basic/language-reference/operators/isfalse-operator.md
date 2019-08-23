---
title: IsFalse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917153"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse — Operator (Visual Basic)
Określa, czy wyrażenie jest `False`.  
  
 Nie można jawnie `IsFalse` wywołać w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z `AndAlso` klauzul. W przypadku zdefiniowania klasy lub struktury, a następnie użycia zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.  
  
 Kompilator traktuje `IsFalse` operatory i `IsTrue` jako pasującą *parę*. Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.  
  
> [!NOTE]
> Operator może być przeciążony, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury. `IsFalse` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje `IsFalse` operatorów i. `IsTrue`  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz także

- [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
