---
title: "Jak interaktywnie kontrolować zegar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: debe65ef1587171dc2f324a19da4b43e7274c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="b2169-102">Jak interaktywnie kontrolować zegar</span><span class="sxs-lookup"><span data-stu-id="b2169-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="b2169-103">A <xref:System.Windows.Media.Animation.Clock> obiektu <xref:System.Windows.Media.Animation.ClockController> właściwość umożliwia interaktywnie uruchamiania, wstrzymać, wznowić, wyszukiwanie, poprawić zegara, aby okresu i zatrzymać zegara.</span><span class="sxs-lookup"><span data-stu-id="b2169-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="b2169-104">Zegar w katalogu głównego drzewa czasu można sterować interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="b2169-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2169-105">Istnieją inne sposoby interaktywnie animacje kontroli niewymagających pracować bezpośrednio z zegary: umożliwia także Scenorys.</span><span class="sxs-lookup"><span data-stu-id="b2169-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="b2169-106">Scenorys są obsługiwane zarówno znaczników i kodu.</span><span class="sxs-lookup"><span data-stu-id="b2169-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="b2169-107">Na przykład zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) lub [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2169-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="b2169-108">W poniższym przykładzie kilka przycisków są używane do sterowania interaktywnego zegara animacji.</span><span class="sxs-lookup"><span data-stu-id="b2169-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2169-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2169-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b2169-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2169-110">See Also</span></span>  
 [<span data-ttu-id="b2169-111">Animować właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="b2169-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="b2169-112">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="b2169-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
