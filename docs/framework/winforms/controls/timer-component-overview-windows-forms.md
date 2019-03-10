---
title: Timer — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: a13afba026f1f9eed095817c65637bb6a091c7f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725288"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="f22e7-102">Timer — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="f22e7-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="f22e7-103">Formularze Windows <xref:System.Windows.Forms.Timer> jest składnikiem, który wywołuje zdarzenie w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="f22e7-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="f22e7-104">Ten składnik jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f22e7-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="f22e7-105">Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f22e7-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="f22e7-106">Kluczowe właściwości, metody i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f22e7-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="f22e7-107">Długość przedziałów jest definiowany przez <xref:System.Windows.Forms.Timer.Interval%2A> właściwość, której wartość jest podana w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="f22e7-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="f22e7-108">Po włączeniu składnika <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest zgłaszane w każdym interwale.</span><span class="sxs-lookup"><span data-stu-id="f22e7-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="f22e7-109">Jest to, gdzie można dodać kod do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f22e7-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="f22e7-110">Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy Windows](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="f22e7-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="f22e7-111">Metody klucza <xref:System.Windows.Forms.Timer> składnik to <xref:System.Windows.Forms.Timer.Start%2A> i <xref:System.Windows.Forms.Timer.Stop%2A>, który czasomierza włączać i wyłączać.</span><span class="sxs-lookup"><span data-stu-id="f22e7-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="f22e7-112">Po wyłączeniu czasomierza resetuje; nie ma możliwości wstrzymania <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="f22e7-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22e7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f22e7-113">See also</span></span>
- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="f22e7-114">Timer, składnik</span><span class="sxs-lookup"><span data-stu-id="f22e7-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="f22e7-115">Ograniczenia właściwości Interval składnika Timer formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f22e7-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
