---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: e1a6cecdf724603b8f4617fe4e8b5ef2c0acdeff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624564"
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
