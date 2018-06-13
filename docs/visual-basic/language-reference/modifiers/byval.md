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
ms.openlocfilehash: 076289ff303dce58f036d6c7cb1505b151da19f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602986"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Określa, że argument jest przekazywany w taki sposób, że wywoływana procedura lub właściwość nie może zmienić wartość zmiennej bazowy argumentu w wywoływanym kodzie.  
  
## <a name="remarks"></a>Uwagi  
 `ByVal` Modyfikatora można używać w tych sytuacjach:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `ByVal` przekazywanie mechanizmu z argumentem typu odwołanie parametru. W tym przykładzie jest argument `c1`, wystąpienie klasy `Class1`. `ByVal` kod w procedurach uniemożliwia zmianę odpowiednia wartość argument odwołania `c1`, ale nie chroni dostępne pola i właściwości `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
