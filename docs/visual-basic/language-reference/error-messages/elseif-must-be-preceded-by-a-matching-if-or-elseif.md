---
title: Instrukcja „#ElseIf” musi być poprzedzona odpowiadającą jej instrukcją „#If” lub „#ElseIf”
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311061"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>Instrukcja „#ElseIf” musi być poprzedzona odpowiadającą jej instrukcją „#If” lub „#ElseIf”
`#ElseIf` jest dyrektywą warunkowa. `#ElseIf` Klauzuli musi być poprzedzona odpowiadającą jej instrukcją `#If` lub `#ElseIf` klauzuli.  
  
 **Identyfikator błędu:** BC30014  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź, czy występuje przed `#If` lub `#ElseIf` nie został rozdzielony ze to `#ElseIf` przez pośredniczące bloku kompilacja warunkowa lub nieprawidłowo umieszczony `#End If`.  
  
2. Jeśli `#ElseIf` jest poprzedzony `#Else` dyrektywy, albo usuń `#Else` lub zmień ją na `#ElseIf`.  
  
3. Jeśli cała reszta będzie w kolejności, należy dodać `#If` dyrektywę na początku bloku kompilacji warunkowej.  
  
## <a name="see-also"></a>Zobacz także

- [#If...Then...#Else — Dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
