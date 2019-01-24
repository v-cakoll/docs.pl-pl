---
title: 'Instrukcje: Kontroluj zegar interaktywnie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 93c2d754ec899c96a50fef3dcef680434f564276
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657548"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="24e1b-102">Instrukcje: Kontroluj zegar interaktywnie</span><span class="sxs-lookup"><span data-stu-id="24e1b-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="24e1b-103">A <xref:System.Windows.Media.Animation.Clock> obiektu <xref:System.Windows.Media.Animation.ClockController> Właściwość pozwala interaktywnie Uruchom, wstrzymać, wznowić, wyszukiwanie, przejdź zegar okresu wypełnienia i zatrzymać zegara.</span><span class="sxs-lookup"><span data-stu-id="24e1b-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="24e1b-104">Tylko zegara głównego drzewa chronometrażu mogą być kontrolowane interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="24e1b-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24e1b-105">Istnieją inne sposoby, aby interaktywnie animacji kontrolki niewymagających współpracować bezpośrednio z zegary: Możesz również użyć scenorysów.</span><span class="sxs-lookup"><span data-stu-id="24e1b-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="24e1b-106">Scenorysy są obsługiwane zarówno w przypadku znaczników, jak i kod.</span><span class="sxs-lookup"><span data-stu-id="24e1b-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="24e1b-107">Aby uzyskać przykład, zobacz [animować właściwość przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) lub [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="24e1b-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="24e1b-108">W poniższym przykładzie kilka przyciski są używane do interaktywnie kontrolować zegar animacji.</span><span class="sxs-lookup"><span data-stu-id="24e1b-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24e1b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="24e1b-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="24e1b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24e1b-110">See also</span></span>
- [<span data-ttu-id="24e1b-111">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="24e1b-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="24e1b-112">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="24e1b-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
