---
title: Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej
Zdarzenie można wywoływane tylko z miejsca deklaracji, w którym jest zadeklarowany. W związku z tym klasy nie mogą wywoływać zdarzeń z żadną inną klasę, nawet jedną, z którego pochodzi.  
  
 **Identyfikator błędu:** BC30029  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś `Event` instrukcji lub `RaiseEvent` instrukcji, dzięki czemu są one w tej samej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
