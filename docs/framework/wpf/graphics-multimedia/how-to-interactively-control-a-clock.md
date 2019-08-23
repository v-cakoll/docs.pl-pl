---
title: 'Instrukcje: Interakcyjne sterowanie zegarem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951335"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="e5502-102">Instrukcje: Interakcyjne sterowanie zegarem</span><span class="sxs-lookup"><span data-stu-id="e5502-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="e5502-103">Właściwość<xref:System.Windows.Media.Animation.ClockController>obiektupozwala interaktywnie uruchamiać, wstrzymywać, wznawiać, poszukiwać, przełączać do jego okresu wypełniania i <xref:System.Windows.Media.Animation.Clock> zatrzymywać zegar.</span><span class="sxs-lookup"><span data-stu-id="e5502-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="e5502-104">Tylko zegar główny drzewa chronometrażu może być interaktywnie kontrolowany.</span><span class="sxs-lookup"><span data-stu-id="e5502-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5502-105">Istnieją inne sposoby interaktywnej kontroli animacji, które nie wymagają bezpośredniej pracy z zegarami: można również użyć scenorysów.</span><span class="sxs-lookup"><span data-stu-id="e5502-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="e5502-106">Scenorysy są obsługiwane zarówno w znacznikach, jak i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e5502-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="e5502-107">Aby zapoznać się z przykładem, zobacz [Animuj Właściwość za pomocą scenorysu](how-to-animate-a-property-by-using-a-storyboard.md) lub [Przegląd animacji](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e5502-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="e5502-108">W poniższym przykładzie kilka przycisków służy do interaktywnego sterowania zegarem animacji.</span><span class="sxs-lookup"><span data-stu-id="e5502-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5502-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5502-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="e5502-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5502-110">See also</span></span>

- [<span data-ttu-id="e5502-111">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="e5502-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="e5502-112">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="e5502-112">Animation Overview</span></span>](animation-overview.md)
