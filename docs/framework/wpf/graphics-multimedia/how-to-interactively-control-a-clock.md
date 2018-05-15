---
title: Jak interaktywnie kontrolować zegar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 63e72c48afd9b72a6b334ccdc234d08cef7288f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="c0588-102">Jak interaktywnie kontrolować zegar</span><span class="sxs-lookup"><span data-stu-id="c0588-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="c0588-103">A <xref:System.Windows.Media.Animation.Clock> obiektu <xref:System.Windows.Media.Animation.ClockController> właściwość umożliwia interaktywnie uruchamiania, wstrzymać, wznowić, wyszukiwanie, poprawić zegara, aby okresu i zatrzymać zegara.</span><span class="sxs-lookup"><span data-stu-id="c0588-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="c0588-104">Zegar w katalogu głównego drzewa czasu można sterować interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="c0588-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0588-105">Istnieją inne sposoby interaktywnie animacje kontroli niewymagających pracować bezpośrednio z zegary: umożliwia także Scenorys.</span><span class="sxs-lookup"><span data-stu-id="c0588-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="c0588-106">Scenorys są obsługiwane zarówno znaczników i kodu.</span><span class="sxs-lookup"><span data-stu-id="c0588-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="c0588-107">Na przykład zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) lub [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c0588-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="c0588-108">W poniższym przykładzie kilka przycisków są używane do sterowania interaktywnego zegara animacji.</span><span class="sxs-lookup"><span data-stu-id="c0588-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0588-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0588-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="c0588-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0588-110">See Also</span></span>  
 [<span data-ttu-id="c0588-111">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="c0588-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="c0588-112">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="c0588-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
