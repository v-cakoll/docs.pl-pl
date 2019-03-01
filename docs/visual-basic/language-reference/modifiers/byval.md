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
ms.openlocfilehash: edee47e41ca78175a6fb24ed5eac255c03de0901
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972579"
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
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a>Zobacz także
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
