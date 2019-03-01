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
ms.openlocfilehash: 91bded2f1249bfcbeeca28419ee9bcec819babf6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965427"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="da88c-102">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da88c-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="da88c-103">Ten temat zawiera listę typowych problemów, które wynikają z programami obsługi zdarzeń w składników odziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="da88c-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="da88c-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="da88c-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="da88c-105">Kod w obsłudze zdarzeń wykonuje się dwa razy dla każdego wywołania</span><span class="sxs-lookup"><span data-stu-id="da88c-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="da88c-106">Program obsługi zdarzeń dziedziczonych nie może zawierać [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="da88c-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="da88c-107">Metoda w klasie bazowej jest już skojarzony ze zdarzeniem i nastąpi odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="da88c-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="da88c-108">Usuń `Handles` klauzuli od dziedziczonej metody.</span><span class="sxs-lookup"><span data-stu-id="da88c-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
-   <span data-ttu-id="da88c-109">Jeśli nie ma dziedziczonej metody `Handles` — słowo kluczowe, sprawdź, czy kod zawiera dodatkowy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) lub dodatkowe metody, które obsługują te same zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="da88c-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da88c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da88c-110">See also</span></span>
- [<span data-ttu-id="da88c-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="da88c-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
