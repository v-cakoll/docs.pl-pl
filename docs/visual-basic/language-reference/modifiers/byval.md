---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Określa, że argument jest przekazywany w taki sposób, że wywoływana procedura lub właściwość nie może zmienić wartość zmiennej bazowy argumentu w wywoływanym kodzie.  
  
## <a name="remarks"></a>Uwagi  
 `ByVal` Modyfikatora można używać w tych sytuacjach:  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `ByVal` przekazywanie mechanizmu z argumentem typu odwołanie parametru. W tym przykładzie jest argument `c1`, wystąpienie klasy `Class1`. `ByVal`kod w procedurach uniemożliwia zmianę odpowiednia wartość argument odwołania `c1`, ale nie chroni dostępne pola i właściwości `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
