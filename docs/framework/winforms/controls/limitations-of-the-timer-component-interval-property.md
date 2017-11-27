---
title: "Ograniczenia składnika Timer formularzy systemu Windows &#39; właściwości interwału s"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72af16b7dcb7709dd132a3748a454eda57acc168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="5487c-102">Ograniczenia składnika Timer formularzy systemu Windows &#39; właściwości interwału s</span><span class="sxs-lookup"><span data-stu-id="5487c-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="5487c-103">Formularze systemu Windows <xref:System.Windows.Forms.Timer> składnik ma <xref:System.Windows.Forms.Timer.Interval%2A> właściwość, która określa liczbę milisekund, jaką między zdarzenie czasomierza jednego i drugiego.</span><span class="sxs-lookup"><span data-stu-id="5487c-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="5487c-104">Jeśli składnik jest wyłączony, czasomierz będzie nadal otrzymywał <xref:System.Windows.Forms.Timer.Tick> zdarzeń w przybliżeniu równe odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="5487c-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="5487c-105">Ten składnik jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5487c-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="5487c-106">Jeśli potrzebujesz czasomierza, które jest odpowiednie dla środowiska serwera, zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="5487c-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="5487c-107">Właściwości interwału</span><span class="sxs-lookup"><span data-stu-id="5487c-107">The Interval Property</span></span>  
 <span data-ttu-id="5487c-108"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość ma kilka ograniczeń dotyczących należy wziąć pod uwagę, gdy są programowania <xref:System.Windows.Forms.Timer> składnika:</span><span class="sxs-lookup"><span data-stu-id="5487c-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="5487c-109">Jeśli aplikacji lub innej aplikacji jest wprowadzenie duże zapotrzebowanie na komputerze — takie jak pętle długie, znacznym obliczeń, lub dysk, sieci lub dostępu do portu — aplikacji nie może pobrać zdarzenia tyle razy, jako <xref:System.Windows.Forms.Timer.Interval%2A> określa właściwości.</span><span class="sxs-lookup"><span data-stu-id="5487c-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="5487c-110">Interwał nie jest gwarantowana upłynąć dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="5487c-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="5487c-111">W celu zapewnienia dokładność, czasomierza powinien sprawdzić zegara systemowego zgodnie z potrzebami, a nie spróbuj do śledzenia skumulowany czas wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="5487c-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="5487c-112">Dokładność <xref:System.Windows.Forms.Timer.Interval%2A> właściwości jest podana w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="5487c-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="5487c-113">Niektóre komputery zawierają wysokiej rozdzielczości licznik o rozdzielczości wyższej niż milisekund.</span><span class="sxs-lookup"><span data-stu-id="5487c-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="5487c-114">Dostępność tych liczników jest zależna od sprzętu procesora komputera.</span><span class="sxs-lookup"><span data-stu-id="5487c-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="5487c-115">Aby uzyskać więcej informacji zobacz artykuł 172338, "Jak Użyj QueryPerformanceCounter do czasu kod," w bazie wiedzy Microsoft Knowledge Base pod adresem http://support.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="5487c-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5487c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5487c-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="5487c-117">Timer — składnik</span><span class="sxs-lookup"><span data-stu-id="5487c-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="5487c-118">Timer — informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="5487c-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
