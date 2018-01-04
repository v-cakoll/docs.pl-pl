---
title: "Jak animować właściwość przy użyciu AnimationClock"
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
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145ff1be88f1af6692a8cf374e871479ed38d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="130c6-102">Jak animować właściwość przy użyciu AnimationClock</span><span class="sxs-lookup"><span data-stu-id="130c6-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="130c6-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.Clock> obiekty do animowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="130c6-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="130c6-104">Istnieją trzy sposoby do animowania właściwości zależności:</span><span class="sxs-lookup"><span data-stu-id="130c6-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="130c6-105">Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> i powiązać ją z tej właściwości przy użyciu <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="130c6-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="130c6-106">Użyj obiektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodę, aby zastosować jedną <xref:System.Windows.Media.Animation.AnimationTimeline> do właściwości docelowej.</span><span class="sxs-lookup"><span data-stu-id="130c6-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="130c6-107">Utwórz <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> i zastosować je do właściwości.</span><span class="sxs-lookup"><span data-stu-id="130c6-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="130c6-108"><xref:System.Windows.Media.Animation.Storyboard>obiekty i <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody umożliwiają animowania właściwości bez bezpośredniego tworzenia i dystrybuowania zegary (przykłady można znaleźć [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) i [animowania właściwości bez Przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); zegary są tworzone i automatycznie dystrybuowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="130c6-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="130c6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="130c6-109">Example</span></span>  
 <span data-ttu-id="130c6-110">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do dwóch podobnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="130c6-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="130c6-111">Na przykład przedstawiający sposób kontrolowania interaktywnie <xref:System.Windows.Media.Animation.Clock> po jej uruchomieniu, zobacz [interaktywnie sterować zegar](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="130c6-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130c6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="130c6-112">See Also</span></span>  
 [<span data-ttu-id="130c6-113">Animowanie właściwości przy użyciu scenorysu</span><span class="sxs-lookup"><span data-stu-id="130c6-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="130c6-114">Animowanie właściwości bez użycia scenorysu</span><span class="sxs-lookup"><span data-stu-id="130c6-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="130c6-115">Techniki animacji właściwości — przegląd</span><span class="sxs-lookup"><span data-stu-id="130c6-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
