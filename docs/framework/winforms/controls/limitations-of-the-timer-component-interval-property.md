---
title: Ograniczenia właściwości interwału składnika czasomierza
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745235"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="61acd-102">Ograniczenia właściwości Interval składnika Timer formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="61acd-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="61acd-103">Składnik <xref:System.Windows.Forms.Timer> Windows Forms ma właściwość <xref:System.Windows.Forms.Timer.Interval%2A>, która określa liczbę milisekund, które przechodzą między zdarzenie czasomierza a następnym.</span><span class="sxs-lookup"><span data-stu-id="61acd-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="61acd-104">O ile składnik nie jest wyłączony, czasomierz nadal otrzymuje zdarzenie <xref:System.Windows.Forms.Timer.Tick> w mniej równych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="61acd-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="61acd-105">Ten składnik jest przeznaczony dla środowiska Windows Formsowego.</span><span class="sxs-lookup"><span data-stu-id="61acd-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="61acd-106">Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="61acd-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="61acd-107">Właściwość Interval</span><span class="sxs-lookup"><span data-stu-id="61acd-107">The Interval Property</span></span>  
 <span data-ttu-id="61acd-108">Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> ma kilka ograniczeń, które należy wziąć pod uwagę podczas programowania składnika <xref:System.Windows.Forms.Timer>:</span><span class="sxs-lookup"><span data-stu-id="61acd-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="61acd-109">Jeśli aplikacja lub inna aplikacja wykonuje duże wymagania w systemie, takich jak długotrwałe pętle, obliczenia intensywnie korzystające z dysku, sieci lub dostępu do portów, aplikacja może nie pobierać zdarzeń czasomierza tak często, jak określa właściwość <xref:System.Windows.Forms.Timer.Interval%2A>.</span><span class="sxs-lookup"><span data-stu-id="61acd-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="61acd-110">Interwał nie jest gwarantowany do upływu czasu.</span><span class="sxs-lookup"><span data-stu-id="61acd-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="61acd-111">Aby zapewnić dokładność, czasomierz powinien sprawdzić zegar systemu zgodnie z wymaganiami, zamiast próbować śledzić skumulowany czas wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="61acd-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="61acd-112">Precyzja właściwości <xref:System.Windows.Forms.Timer.Interval%2A> jest w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="61acd-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="61acd-113">Niektóre komputery zapewniają licznik o wysokiej rozdzielczości o rozdzielczości większej niż milisekundy.</span><span class="sxs-lookup"><span data-stu-id="61acd-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="61acd-114">Dostępność takiego licznika zależy od sprzętu procesora komputera.</span><span class="sxs-lookup"><span data-stu-id="61acd-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="61acd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61acd-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="61acd-116">Timer, składnik</span><span class="sxs-lookup"><span data-stu-id="61acd-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="61acd-117">Timer, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="61acd-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
