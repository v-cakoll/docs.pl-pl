---
title: 'Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: e4132f51f4dd85ad964042d05f7c5bc0a2e6e3cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826629"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="e2f06-102">Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2f06-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="e2f06-103">Istnieje kilka sytuacji po ważne jest, że aplikacja niskich jej użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2f06-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="e2f06-104">Zdarzenia niestandardowe Zezwól aplikacji na potrzeby pamięci tylko zdarzenia, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="e2f06-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="e2f06-105">Domyślnie gdy klasa deklaruje zdarzenie, kompilator przydziela pamięć dla pola do przechowywania informacji o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="e2f06-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="e2f06-106">Jeśli klasa ma wiele zdarzeń nieużywane, niepotrzebnie zajmowały pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2f06-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="e2f06-107">Zamiast Domyślna implementacja zdarzeń, które zapewnia Visual Basic, można użyć zdarzeń niestandardowych do bardziej dokładnie zarządzać wykorzystaniem pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2f06-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2f06-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2f06-108">Example</span></span>  
 <span data-ttu-id="e2f06-109">W tym przykładzie klasa używa jednego wystąpienia <xref:System.ComponentModel.EventHandlerList> klasy, przechowywane w `Events` pola do przechowywania informacji o zdarzeniach w użyciu.</span><span class="sxs-lookup"><span data-stu-id="e2f06-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="e2f06-110"><xref:System.ComponentModel.EventHandlerList> Klasa jest klasą zoptymalizowane listy przeznaczone do przechowywania delegatów.</span><span class="sxs-lookup"><span data-stu-id="e2f06-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="e2f06-111">Wszystkie zdarzenia z użyciem klasy `Events` pola do śledzenia metod obsługi każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e2f06-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="e2f06-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2f06-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="e2f06-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e2f06-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="e2f06-114">Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania</span><span class="sxs-lookup"><span data-stu-id="e2f06-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
