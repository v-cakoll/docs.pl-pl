---
title: Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: e7c56757d18a22a65b4ef8e81d2a05e5f4f4dffc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680208"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic
Ten temat zawiera listę typowych problemów, które wynikają z programami obsługi zdarzeń w składników odziedziczonych.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Kod w obsłudze zdarzeń wykonuje się dwa razy dla każdego wywołania  
  
-   Program obsługi zdarzeń dziedziczonych nie może zawierać [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli. Metoda w klasie bazowej jest już skojarzony ze zdarzeniem i nastąpi odpowiednio. Usuń `Handles` klauzuli od dziedziczonej metody.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Jeśli nie ma dziedziczonej metody `Handles` — słowo kluczowe, sprawdź, czy kod zawiera dodatkowy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) lub dodatkowe metody, które obsługują te same zdarzenia.  
  
## <a name="see-also"></a>Zobacz także
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
