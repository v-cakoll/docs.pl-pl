---
title: Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
Zmienna zadeklarowana ze `Shared` modyfikator jest udostępniona zmienna. Udostępniona zmienna identyfikuje dokładnie jedną lokalizację magazynu. Zmienna zadeklarowana ze `WithEvents` modyfikator potwierdza, że typ, do której należy zmienna obsługuje zbioru zdarzeń zgłasza zmiennej. Gdy wartość jest przypisany do zmiennej, właściwość utworzone przez `WithEvents` deklaracji unhooks dowolnego istniejącego programu obsługi zdarzeń i przechwytuje się nowy program obsługi zdarzeń za pomocą `Add` metody.  
  
 **Identyfikator błędu:** BC30594  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zadeklaruj procedury obsługi zdarzenia `Shared`.  
  
## <a name="see-also"></a>Zobacz też  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
