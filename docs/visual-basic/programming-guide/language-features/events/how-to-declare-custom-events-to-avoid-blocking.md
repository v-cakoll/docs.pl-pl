---
title: "Porady: deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="7f9fa-102">Porady: deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9fa-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="7f9fa-103">Istnieją kilka okoliczności, gdy należy pamiętać, że jedna procedura obsługi zdarzeń blokuje obsługi kolejnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="7f9fa-104">Zdarzenia niestandardowe umożliwiają zdarzenia asynchroniczne wywoływanie jej obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="7f9fa-105">Domyślnie pole magazynu zapasowego deklaracji zdarzenia jest multiemisji delegata, który kolejno łączy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="7f9fa-106">Oznacza to, że jeśli jednej procedury obsługi trwa długo, blokuje innych programów obsługi dopóki nie ukończy.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="7f9fa-107">(Procedury obsługi zdarzeń dobrze działające nigdy nie należy wykonywać operacje długie lub potencjalnie blokujące.)</span><span class="sxs-lookup"><span data-stu-id="7f9fa-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="7f9fa-108">Zamiast Domyślna implementacja zdarzeń, które zapewnia Visual Basic, niestandardowe zdarzenia można używać do wykonywania programów obsługi zdarzeń asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f9fa-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f9fa-109">Example</span></span>  
 <span data-ttu-id="7f9fa-110">W tym przykładzie `AddHandler` akcesor dodaje delegowanie dla każdego obsługi `Click` zdarzenia <xref:System.Collections.ArrayList> przechowywane w `EventHandlerList` pola.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="7f9fa-111">Gdy kod generuje `Click` zdarzeń, `RaiseEvent` akcesor wywołuje wszystkie delegatów obsługi zdarzeń asynchronicznie za pomocą <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="7f9fa-112">Ta metoda wywołuje każdy program obsługi na wątku roboczego i zwraca natychmiast, więc obsługi nie można zablokować siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="7f9fa-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7f9fa-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f9fa-113">See Also</span></span>  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [<span data-ttu-id="7f9fa-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7f9fa-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="7f9fa-115">Porady: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci</span><span class="sxs-lookup"><span data-stu-id="7f9fa-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
