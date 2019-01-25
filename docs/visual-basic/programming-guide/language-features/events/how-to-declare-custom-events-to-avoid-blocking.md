---
title: 'Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: e1fed68f4abffb0e20230f55b0ddeffc63f7c78d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691547"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="fa3fc-102">Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa3fc-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="fa3fc-103">Istnieją kilka okoliczności, gdy jest ważne, że jedna procedura obsługi zdarzeń blokuje obsługi kolejnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="fa3fc-104">Zdarzenia niestandardowe umożliwiają zdarzenia asynchroniczne wywoływanie swoich programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="fa3fc-105">Domyślnie pole Magazyn zapasowy deklaracji zdarzenia jest multiemisji delegat, który łączy szeregowo wszystkich procedur obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="fa3fc-106">Oznacza to, że jeśli jeden program obsługi zajmuje dużo czasu, blokuje innych programów obsługi przed zakończeniem tego procesu.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="fa3fc-107">(Procedury obsługi zdarzeń dobrze działające nigdy nie należy wykonywać operacji długotrwałej lub mogącego powodować blokowanie.)</span><span class="sxs-lookup"><span data-stu-id="fa3fc-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="fa3fc-108">Zamiast Domyślna implementacja zdarzeń, które zapewnia Visual Basic, można użyć niestandardowego zdarzenia asynchroniczne wykonywanie procedur obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa3fc-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa3fc-109">Example</span></span>  
 <span data-ttu-id="fa3fc-110">W tym przykładzie `AddHandler` akcesor dodaje delegata dla każdego program obsługi `Click` zdarzenia <xref:System.Collections.ArrayList> przechowywane w `EventHandlerList` pola.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="fa3fc-111">Gdy kod wywołuje `Click` zdarzenia `RaiseEvent` akcesor wywołuje wszystkie delegatów obsługi zdarzeń asynchronicznie za pomocą <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="fa3fc-112">Ta metoda wywołuje każdy program obsługi w wątku roboczego i zwraca wynik natychmiast, więc obsługi nie można zablokować siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="fa3fc-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fa3fc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa3fc-113">See also</span></span>
- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="fa3fc-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fa3fc-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="fa3fc-115">Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci</span><span class="sxs-lookup"><span data-stu-id="fa3fc-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
