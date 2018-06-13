---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 240058a534456ae20c9c129a068bae575ac45eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596011"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Określa, że co najmniej jeden zadeklarowana zmienna elementu członkowskiego odwołują się do wystąpienia klasy, które może wywoływać zdarzenia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zmienna jest zdefiniowana za pomocą `WithEvents`, deklaratywnego można określić zdarzenia zmiennej przy użyciu obsługiwała `Handles` — słowo kluczowe.  
  
 Można użyć `WithEvents` tylko na poziomie klasę lub moduł. Oznacza to, że w kontekście deklaracji `WithEvents` zmiennej musi być klasą lub modułu i nie może być plik źródłowy, przestrzeni nazw, struktury lub procedury.  
  
 Nie można użyć `WithEvents` dla elementu członkowskiego struktury.  
  
 Można zadeklarować tylko pojedyncze zmienne — nie stałych — z `WithEvents`.  
  
## <a name="rules"></a>Reguły  
  
-   **Typy elementów.** Musisz zadeklarować `WithEvents` zmienne, które mają być obiekt zmienne, tak aby mogą akceptować klasy wystąpień. Jednak nie można zadeklarować je jako `Object`. Musisz zadeklarować je jako określonej klasy, które może wywoływać zdarzenia.  
  
 `WithEvents` Modyfikatora można używać w tym kontekście: [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Uchwyty](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
