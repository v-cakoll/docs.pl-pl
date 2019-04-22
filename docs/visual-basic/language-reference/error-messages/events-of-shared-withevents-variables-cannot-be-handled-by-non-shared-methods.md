---
title: Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838654"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
Zmienna zadeklarowana ze `Shared` modyfikator jest udostępnionej zmiennej. Udostępnionej zmiennej identyfikuje dokładnie jednej lokalizacji magazynu. Zmienna zadeklarowana ze `WithEvents` modyfikator potwierdza, że typ, do której należy zmiennej obsługuje zbioru zdarzeń wywołuje zmienną. Gdy wartość jest przypisany do zmiennej, właściwość utworzone przez `WithEvents` deklaracja unhooks dowolnego istniejącego programu obsługi zdarzeń i przechwytuje się nowa procedura obsługi zdarzeń za pośrednictwem `Add` metody.  
  
 **Identyfikator błędu:** BC30594  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zadeklaruj procedury obsługi zdarzenia `Shared`.  
  
## <a name="see-also"></a>Zobacz także

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
