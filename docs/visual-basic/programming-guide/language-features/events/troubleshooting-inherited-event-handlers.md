---
title: "Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e8f0b669566bbee6530931bfba9808fad0c085
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic
Ten temat zawiera listę typowych problemów, które wynikają z obsługi zdarzeń w składników odziedziczonych.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Wykonuje kod w obsłudze zdarzeń dwukrotnie dla każdego wywołania  
  
-   Program obsługi zdarzeń dziedziczone nie mogą zawierać [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli. Metoda w klasie podstawowej jest już skojarzona ze zdarzeniem i będą uruchamiane w związku z tym. Usuń `Handles` klauzuli od dziedziczonej metody.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Jeśli nie ma dziedziczonej metody `Handles` — słowo kluczowe, sprawdź, czy kod zawiera dodatkowy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) lub dodatkowe metody, które obsługują tego samego zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
