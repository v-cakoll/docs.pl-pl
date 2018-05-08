---
title: '&#39;#ElseIf&#39; musi być poprzedzona odpowiadającą jej instrukcją &#39;#If&#39; lub &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: ef904173b1791309f6c2722bd959cabdad1d71da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39;#ElseIf&#39; musi być poprzedzona odpowiadającą jej instrukcją &#39;#If&#39; lub &#39;#ElseIf&#39;
`#ElseIf` jest warunkowej dyrektywie kompilacji. `#ElseIf` Klauzuli musi być poprzedzona odpowiadającą jej instrukcją `#If` lub `#ElseIf` klauzuli.  
  
 **Identyfikator błędu:** BC30014  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy występuje przed `#If` lub `#ElseIf` nie został oddzielony od to `#ElseIf` przez pośredniczące bloku kompilacja warunkowa lub niewłaściwie umieszczony `#End If`.  
  
2.  Jeśli `#ElseIf` jest poprzedzony `#Else` dyrektywy, Usuń `#Else` lub zmień, aby `#ElseIf`.  
  
3.  W przypadku wszystkich pozostałych w kolejności, Dodaj `#If` dyrektywy na początku bloku kompilacji warunkowej.  
  
## <a name="see-also"></a>Zobacz też  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
