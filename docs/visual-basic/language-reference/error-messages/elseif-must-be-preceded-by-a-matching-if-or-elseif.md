---
title: '&#39;#ElseIf&#39; musi być poprzedzona odpowiadającą jej instrukcją &#39;#If&#39; lub &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 1e63595ee573e9356f6870a02b2131897c725baf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505786"
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39;#ElseIf&#39; musi być poprzedzona odpowiadającą jej instrukcją &#39;#If&#39; lub &#39;#ElseIf&#39;
`#ElseIf` jest dyrektywą warunkowa. `#ElseIf` Klauzuli musi być poprzedzona odpowiadającą jej instrukcją `#If` lub `#ElseIf` klauzuli.  
  
 **Identyfikator błędu:** BC30014  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy występuje przed `#If` lub `#ElseIf` nie został rozdzielony ze to `#ElseIf` przez pośredniczące bloku kompilacja warunkowa lub nieprawidłowo umieszczony `#End If`.  
  
2.  Jeśli `#ElseIf` jest poprzedzony `#Else` dyrektywy, albo usuń `#Else` lub zmień ją na `#ElseIf`.  
  
3.  Jeśli cała reszta będzie w kolejności, należy dodać `#If` dyrektywę na początku bloku kompilacji warunkowej.  
  
## <a name="see-also"></a>Zobacz także
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
