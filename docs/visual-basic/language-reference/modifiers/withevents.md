---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826616"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Określa, że co najmniej jednej zmiennej zadeklarowanej składowej odnoszą się do wystąpienia klasy, które może wywoływać zdarzenia.  
  
## <a name="remarks"></a>Uwagi  
 Gdy zmienna jest zdefiniowana za pomocą `WithEvents`, deklaratywne określenie, zmiennej na zdarzenia przy użyciu obsługiwała `Handles` — słowo kluczowe.  
  
 Możesz użyć `WithEvents` tylko na poziomie klasy lub modułu. Oznacza to, że kontekst deklaracji `WithEvents` zmienna musi być klasą lub moduł i nie może być plikiem źródłowym, przestrzeni nazw, struktura lub procedury.  
  
 Nie można użyć `WithEvents` członka struktury.  
  
 Można zadeklarować tylko zmienne poszczególnych — tablice nie — z `WithEvents`.  
  
## <a name="rules"></a>reguły  
  
-   **Typy elementów.** Musisz zadeklarować `WithEvents` zmienne jako zmienne do obiektu, dzięki czemu mogą akceptować klasy wystąpień. Jednak nie można zadeklarować je jako `Object`. Musisz je zadeklarować jako określonej klasy, które może wywoływać zdarzenia.  
  
 `WithEvents` Modyfikatora można używać w tym kontekście: [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
