---
title: Timer — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742782"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="b0518-102">Timer — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="b0518-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b0518-103"><xref:System.Windows.Forms.Timer> Windows Forms jest składnikiem, który wywołuje zdarzenie w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="b0518-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="b0518-104">Ten składnik jest przeznaczony dla środowiska Windows Formsowego.</span><span class="sxs-lookup"><span data-stu-id="b0518-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="b0518-105">Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b0518-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="b0518-106">Właściwości klucza, metody i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b0518-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="b0518-107">Długość interwałów jest definiowana przez właściwość <xref:System.Windows.Forms.Timer.Interval%2A>, której wartość jest wyrażona w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="b0518-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="b0518-108">Po włączeniu składnika <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest zgłaszane każdy interwał.</span><span class="sxs-lookup"><span data-stu-id="b0518-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="b0518-109">Jest to miejsce, w którym można dodać kod do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b0518-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="b0518-110">Aby uzyskać więcej informacji, zobacz [jak: uruchamiać procedury w określonych odstępach czasu za pomocą składnika czasomierza Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="b0518-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="b0518-111">Kluczowe metody składnika <xref:System.Windows.Forms.Timer> są <xref:System.Windows.Forms.Timer.Start%2A> i <xref:System.Windows.Forms.Timer.Stop%2A>, co powoduje włączenie i wyłączenie czasomierza.</span><span class="sxs-lookup"><span data-stu-id="b0518-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="b0518-112">Gdy czasomierz zostanie wyłączony, resetuje; nie istnieje sposób, aby wstrzymywać składnik <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="b0518-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0518-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0518-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="b0518-114">Timer, składnik</span><span class="sxs-lookup"><span data-stu-id="b0518-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="b0518-115">Ograniczenia właściwości Interval składnika Timer formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0518-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
