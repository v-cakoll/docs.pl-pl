---
title: "IsFalse — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d85fc51a75f82c65cf226b8239a8eee6585bd18a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [IsTrue — Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Porady: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [AndAlso — Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
