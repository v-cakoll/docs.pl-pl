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
ms.openlocfilehash: f6355cf7fc2e43651c1112d048220a8179968c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646334"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="434ee-102">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="434ee-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="434ee-103">Ten temat zawiera listę typowych problemów, które wynikają z obsługi zdarzeń w składników odziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="434ee-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="434ee-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="434ee-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="434ee-105">Wykonuje kod w obsłudze zdarzeń dwukrotnie dla każdego wywołania</span><span class="sxs-lookup"><span data-stu-id="434ee-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="434ee-106">Program obsługi zdarzeń dziedziczone nie mogą zawierać [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="434ee-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="434ee-107">Metoda w klasie podstawowej jest już skojarzona ze zdarzeniem i będą uruchamiane w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="434ee-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="434ee-108">Usuń `Handles` klauzuli od dziedziczonej metody.</span><span class="sxs-lookup"><span data-stu-id="434ee-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="434ee-109">Jeśli nie ma dziedziczonej metody `Handles` — słowo kluczowe, sprawdź, czy kod zawiera dodatkowy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) lub dodatkowe metody, które obsługują tego samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="434ee-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434ee-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="434ee-110">See Also</span></span>  
 [<span data-ttu-id="434ee-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="434ee-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
