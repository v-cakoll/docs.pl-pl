---
title: Ograniczenia właściwości Interval składnika Timer formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: f564a4ce7fa2d9b8ea5446f2cf6bd016db054dd9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724391"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="4f5ce-102">Ograniczenia właściwości Interval składnika Timer formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4f5ce-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="4f5ce-103">Formularze Windows <xref:System.Windows.Forms.Timer> składnik ma <xref:System.Windows.Forms.Timer.Interval%2A> właściwość, która określa liczbę milisekund, które przechodzą między zdarzenie czasomierza jeden, a następnie.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="4f5ce-104">Jeśli składnik jest wyłączony, czasomierz w dalszym ciągu otrzymywać <xref:System.Windows.Forms.Timer.Tick> zdarzeń w przybliżeniu jednakowej odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="4f5ce-105">Ten składnik jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="4f5ce-106">Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4f5ce-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="4f5ce-107">Właściwości interwału</span><span class="sxs-lookup"><span data-stu-id="4f5ce-107">The Interval Property</span></span>  
 <span data-ttu-id="4f5ce-108"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość ma pewne ograniczenia, które należy wziąć pod uwagę podczas programowania <xref:System.Windows.Forms.Timer> składników:</span><span class="sxs-lookup"><span data-stu-id="4f5ce-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="4f5ce-109">Jeśli aplikacja lub innej aplikacji wysokimi wymaganiami w systemie — takiej jak długo pętli, intensywnie korzystających z obliczeń, dysków, sieci lub dostępu do portu — aplikacja nie może pobrać zdarzenia czasomierza, tak często, jak <xref:System.Windows.Forms.Timer.Interval%2A> określa właściwości.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="4f5ce-110">Interwał nie musi upłynąć dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="4f5ce-111">W celu zapewnienia dokładności, czasomierz powinien sprawdzanie zegara systemowego zgodnie z potrzebami, a nie spróbuj śledzić czas skumulowana wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="4f5ce-112">Dokładność <xref:System.Windows.Forms.Timer.Interval%2A> właściwość jest podana w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="4f5ce-113">Niektóre komputery udostępniają licznika o wysokiej rozdzielczości o rozdzielczości wyższej niż milisekund.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="4f5ce-114">Dostępność tych liczników jest zależna od sprzętu procesora komputera.</span><span class="sxs-lookup"><span data-stu-id="4f5ce-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f5ce-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f5ce-115">See also</span></span>
- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="4f5ce-116">Timer, składnik</span><span class="sxs-lookup"><span data-stu-id="4f5ce-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="4f5ce-117">Timer, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="4f5ce-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
