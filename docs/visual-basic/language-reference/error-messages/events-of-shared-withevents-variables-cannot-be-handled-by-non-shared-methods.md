---
title: Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 09f56d340322ee88afc54e7e8a53716777782d47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505773"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
Zmienna zadeklarowana ze `Shared` modyfikator jest udostępnionej zmiennej. Udostępnionej zmiennej identyfikuje dokładnie jednej lokalizacji magazynu. Zmienna zadeklarowana ze `WithEvents` modyfikator potwierdza, że typ, do której należy zmiennej obsługuje zbioru zdarzeń wywołuje zmienną. Gdy wartość jest przypisany do zmiennej, właściwość utworzone przez `WithEvents` deklaracja unhooks dowolnego istniejącego programu obsługi zdarzeń i przechwytuje się nowa procedura obsługi zdarzeń za pośrednictwem `Add` metody.  
  
 **Identyfikator błędu:** BC30594  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zadeklaruj procedury obsługi zdarzenia `Shared`.  
  
## <a name="see-also"></a>Zobacz także
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
