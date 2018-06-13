---
title: Timer — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 39bc3c8cda06a62eb40b042e46cbd070a82cce01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535505"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="15b2c-102">Timer — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="15b2c-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="15b2c-103">Formularze systemu Windows <xref:System.Windows.Forms.Timer> to składnik, który wywołuje zdarzenie w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="15b2c-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="15b2c-104">Ten składnik jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="15b2c-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="15b2c-105">Jeśli potrzebujesz czasomierza, które jest odpowiednie dla środowiska serwera, zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="15b2c-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="15b2c-106">Właściwości klucza, metod i zdarzeń</span><span class="sxs-lookup"><span data-stu-id="15b2c-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="15b2c-107">Długość przedziałów jest definiowana za pomocą <xref:System.Windows.Forms.Timer.Interval%2A> właściwości, której wartość jest podana w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="15b2c-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="15b2c-108">Po włączeniu składnika <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest zgłaszane, co interwał.</span><span class="sxs-lookup"><span data-stu-id="15b2c-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="15b2c-109">Jest to, gdzie można dodać kod do wykonania.</span><span class="sxs-lookup"><span data-stu-id="15b2c-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="15b2c-110">Aby uzyskać więcej informacji, zobacz [porady: uruchamianie procedur odstępach ustawić za pomocą składnika Timer formularzy systemu Windows](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="15b2c-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="15b2c-111">Metody klucza <xref:System.Windows.Forms.Timer> są składnika <xref:System.Windows.Forms.Timer.Start%2A> i <xref:System.Windows.Forms.Timer.Stop%2A>, które czasomierza Włączanie i wyłączanie.</span><span class="sxs-lookup"><span data-stu-id="15b2c-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="15b2c-112">Po wyłączeniu czasomierza resetuje; nie istnieje sposób wstrzymania <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="15b2c-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b2c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15b2c-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="15b2c-114">Timer, składnik</span><span class="sxs-lookup"><span data-stu-id="15b2c-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="15b2c-115">Ograniczenia właściwości Interval składnika Timer formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15b2c-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
