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
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186592"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="b1ac4-102">Instrukcje: Interakcyjne sterowanie zegarem</span><span class="sxs-lookup"><span data-stu-id="b1ac4-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="b1ac4-103">A <xref:System.Windows.Media.Animation.Clock> obiektu <xref:System.Windows.Media.Animation.ClockController> Właściwość pozwala interaktywnie Uruchom, wstrzymać, wznowić, wyszukiwanie, przejdź zegar okresu wypełnienia i zatrzymać zegara.</span><span class="sxs-lookup"><span data-stu-id="b1ac4-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="b1ac4-104">Tylko zegara głównego drzewa chronometrażu mogą być kontrolowane interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="b1ac4-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1ac4-105">Istnieją inne sposoby, aby interaktywnie animacji kontrolki niewymagających współpracować bezpośrednio z zegary: Możesz również użyć scenorysów.</span><span class="sxs-lookup"><span data-stu-id="b1ac4-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="b1ac4-106">Scenorysy są obsługiwane zarówno w przypadku znaczników, jak i kod.</span><span class="sxs-lookup"><span data-stu-id="b1ac4-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="b1ac4-107">Aby uzyskać przykład, zobacz [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md) lub [Przegląd animacja](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1ac4-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="b1ac4-108">W poniższym przykładzie kilka przyciski są używane do interaktywnie kontrolować zegar animacji.</span><span class="sxs-lookup"><span data-stu-id="b1ac4-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ac4-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1ac4-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b1ac4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1ac4-110">See also</span></span>

- [<span data-ttu-id="b1ac4-111">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="b1ac4-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="b1ac4-112">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="b1ac4-112">Animation Overview</span></span>](animation-overview.md)
