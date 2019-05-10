---
title: 'Instrukcje: Animowanie właściwości przy użyciu elementu AnimationClock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 13d91e8589c40d84ba374ffc613388e24407796a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591289"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="40ce7-102">Instrukcje: Animowanie właściwości przy użyciu elementu AnimationClock</span><span class="sxs-lookup"><span data-stu-id="40ce7-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="40ce7-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.Clock> obiektów, aby animować właściwości.</span><span class="sxs-lookup"><span data-stu-id="40ce7-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="40ce7-104">Istnieją trzy sposoby, aby animować właściwości zależności:</span><span class="sxs-lookup"><span data-stu-id="40ce7-104">There are three ways to animate a dependency property:</span></span>  
  
- <span data-ttu-id="40ce7-105">Tworzenie <xref:System.Windows.Media.Animation.AnimationTimeline> i skojarz go z tej właściwości przy użyciu <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="40ce7-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
- <span data-ttu-id="40ce7-106">Użyj obiektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody do stosowania pojedynczej <xref:System.Windows.Media.Animation.AnimationTimeline> do właściwości docelowej.</span><span class="sxs-lookup"><span data-stu-id="40ce7-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
- <span data-ttu-id="40ce7-107">Tworzenie <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> i zastosować je do właściwości.</span><span class="sxs-lookup"><span data-stu-id="40ce7-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="40ce7-108"><xref:System.Windows.Media.Animation.Storyboard> obiekty i <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody umożliwiają animować właściwości bez bezpośrednio tworzenie i rozpowszechnianie zegary (przykłady można znaleźć [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md) i [animować właściwości bez Za pomocą scenorysu](how-to-animate-a-property-without-using-a-storyboard.md)); zegary są tworzone i dystrybucji dla Ciebie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="40ce7-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40ce7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="40ce7-109">Example</span></span>  
 <span data-ttu-id="40ce7-110">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do dwóch podobnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="40ce7-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="40ce7-111">Aby uzyskać przykład pokazujący sposób interaktywnie kontrolować <xref:System.Windows.Media.Animation.Clock> po jego uruchomieniu, zobacz [interaktywnie kontrolować zegar](how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="40ce7-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ce7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40ce7-112">See also</span></span>

- [<span data-ttu-id="40ce7-113">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="40ce7-113">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="40ce7-114">Animowanie właściwości bez użycia scenorysu</span><span class="sxs-lookup"><span data-stu-id="40ce7-114">Animate a Property Without Using a Storyboard</span></span>](how-to-animate-a-property-without-using-a-storyboard.md)
- [<span data-ttu-id="40ce7-115">Techniki animacji właściwości — przegląd</span><span class="sxs-lookup"><span data-stu-id="40ce7-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
