---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
