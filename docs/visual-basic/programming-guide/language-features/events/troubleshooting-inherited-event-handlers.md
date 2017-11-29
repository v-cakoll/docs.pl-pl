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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="e2fe8-102">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2fe8-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="e2fe8-103">Ten temat zawiera listę typowych problemów, które wynikają z obsługi zdarzeń w składników odziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="e2fe8-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e2fe8-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="e2fe8-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="e2fe8-105">Wykonuje kod w obsłudze zdarzeń dwukrotnie dla każdego wywołania</span><span class="sxs-lookup"><span data-stu-id="e2fe8-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="e2fe8-106">Program obsługi zdarzeń dziedziczone nie mogą zawierać [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e2fe8-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="e2fe8-107">Metoda w klasie podstawowej jest już skojarzona ze zdarzeniem i będą uruchamiane w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="e2fe8-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="e2fe8-108">Usuń `Handles` klauzuli od dziedziczonej metody.</span><span class="sxs-lookup"><span data-stu-id="e2fe8-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="e2fe8-109">Jeśli nie ma dziedziczonej metody `Handles` — słowo kluczowe, sprawdź, czy kod zawiera dodatkowy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) lub dodatkowe metody, które obsługują tego samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e2fe8-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fe8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2fe8-110">See Also</span></span>  
 [<span data-ttu-id="e2fe8-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e2fe8-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
