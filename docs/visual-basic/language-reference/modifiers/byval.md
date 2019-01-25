---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 6fa87db4fbab961dd1aa526e2ac8ff15b031005b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650083"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Określa, że argument jest przekazywany w taki sposób, że wywoływana procedura lub właściwość nie można zmienić wartość zmiennej bazowego argumentu w wywoływanym kodzie.  
  
## <a name="remarks"></a>Uwagi  
 `ByVal` Modyfikator mogą być używane w tych kontekstach:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `ByVal` parametru, przekazując mechanizm, za pomocą argumentu typu odwołania. W tym przykładzie argument jest `c1`, wystąpienie klasy `Class1`. `ByVal` uniemożliwia zmienianie podstawowej wartości argument odwołania przez kod w procedurach `c1`, ale nie chroni dostępnych pól i właściwości działania `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
