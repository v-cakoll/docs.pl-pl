---
title: '&#39;#Region&#39; i &#39;#End Region&#39; nie są prawidłowe w ramach metod treści wielowierszowych wyrażeń lambda'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; i &#39;#End Region&#39; nie są prawidłowe w obrębie metody treści/wielowierszowych wyrażeń lambda
`#Region` Bloku musi być zadeklarowana na poziomie klasy, modułu lub przestrzeni nazw. Region zwijanej mogą zawierać jedną lub więcej procedur, ale go nie może rozpoczynać się ani kończyć wewnątrz procedury.  
  
 **Identyfikator błędu:** BC32025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wcześniejsza procedura jest prawidłowo zakończony z `End Function` lub `End Sub` instrukcji.  
  
2.  Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
