---
title: Zwalnianie funkcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965729"
---
# <a name="easing-functions"></a><span data-ttu-id="425a5-102">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="425a5-102">Easing Functions</span></span>
<span data-ttu-id="425a5-103">Funkcje krzywych napięcia umożliwiają stosowanie niestandardowych formuł matematycznych do animacji.</span><span class="sxs-lookup"><span data-stu-id="425a5-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="425a5-104">Na przykład, możesz chcieć, aby obiekt mógł odbijać lub zachowywać się tak, jakby był on sprężyną.</span><span class="sxs-lookup"><span data-stu-id="425a5-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="425a5-105">Możesz użyć klatek kluczowych lub nawet z/do/przez animacje, aby przybliżyć te efekty, ale zajmiemy się znaczną ilością pracy, a animacja byłaby mniej dokładna niż użycie formuły matematycznej.</span><span class="sxs-lookup"><span data-stu-id="425a5-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="425a5-106">Oprócz tworzenia własnej niestandardowej funkcji napięcia przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>, można użyć jednej z kilku funkcji sterowania zapewnianego przez środowisko uruchomieniowe w celu utworzenia typowych efektów.</span><span class="sxs-lookup"><span data-stu-id="425a5-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="425a5-107"><xref:System.Windows.Media.Animation.BackEase>: Wycofuje ruch animacji nieco przed rozpoczęciem animacji w wskazanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="425a5-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="425a5-108"><xref:System.Windows.Media.Animation.BounceEase>: Tworzy efekt odbijania.</span><span class="sxs-lookup"><span data-stu-id="425a5-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="425a5-109"><xref:System.Windows.Media.Animation.CircleEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu funkcji cyklicznej.</span><span class="sxs-lookup"><span data-stu-id="425a5-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="425a5-110"><xref:System.Windows.Media.Animation.CubicEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="425a5-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="425a5-111"><xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animację, która przypomina sprężynę z powrotem i do przodu, aż do momentu zapełnienia.</span><span class="sxs-lookup"><span data-stu-id="425a5-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="425a5-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły wykładniczej.</span><span class="sxs-lookup"><span data-stu-id="425a5-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="425a5-113"><xref:System.Windows.Media.Animation.PowerEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>p</sup> , <xref:System.Windows.Media.Animation.PowerEase.Power%2A> gdzie p jest równe właściwości.</span><span class="sxs-lookup"><span data-stu-id="425a5-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="425a5-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="425a5-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="425a5-115"><xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="425a5-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="425a5-116"><xref:System.Windows.Media.Animation.QuinticEase>: Utwórz animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="425a5-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="425a5-117"><xref:System.Windows.Media.Animation.SineEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły sinusa.</span><span class="sxs-lookup"><span data-stu-id="425a5-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="425a5-118">Aby zastosować funkcję krzywej napięcia do animacji, użyj `EasingFunction` właściwości animacji Określ funkcję krzywych napięcia, która ma zostać zastosowana do animacji.</span><span class="sxs-lookup"><span data-stu-id="425a5-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="425a5-119">Poniższy przykład stosuje <xref:System.Windows.Media.Animation.BounceEase> funkcję krzywej napięcia do, <xref:System.Windows.Media.Animation.DoubleAnimation> aby utworzyć efekt odbijania.</span><span class="sxs-lookup"><span data-stu-id="425a5-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="425a5-120">W poprzednim przykładzie funkcja napięcia została zastosowana do animacji z/do/przez.</span><span class="sxs-lookup"><span data-stu-id="425a5-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="425a5-121">Można również zastosować te funkcje napięcia do animacji klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="425a5-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="425a5-122">Poniższy przykład pokazuje, jak używać klatek kluczowych z funkcją krzywych napięcia skojarzonych z nimi w celu utworzenia animacji prostokąta, który zawiera kontrakty w górę, spowalnia działanie, a następnie rozwija w dół (w przypadku spadku), a następnie odbija do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="425a5-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="425a5-123">Można użyć <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> właściwości, aby zmienić sposób zachowania funkcji krzywej napięcia, czyli zmienić sposób interpolacji animacji.</span><span class="sxs-lookup"><span data-stu-id="425a5-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="425a5-124">Dostępne są trzy możliwe wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="425a5-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="425a5-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacja następuje po formule matematycznej skojarzonej z funkcją krzywych napięcia.</span><span class="sxs-lookup"><span data-stu-id="425a5-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="425a5-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacja następuje po 100% interpolacji minus wynik formuły skojarzonej z funkcją krzywej napięcia.</span><span class="sxs-lookup"><span data-stu-id="425a5-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="425a5-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolacja stosuje <xref:System.Windows.Media.Animation.EasingMode.EaseIn> się w pierwszej połowie animacji, a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> druga połowa.</span><span class="sxs-lookup"><span data-stu-id="425a5-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="425a5-128">Poniższe wykresy przedstawiają różne wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> , gdzie *f*(*x*) reprezentuje postęp animacji, a czas .</span><span class="sxs-lookup"><span data-stu-id="425a5-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="425a5-129">![Wykresy] krzywych napięcia (./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="425a5-130">![Wykresy krzywych napięcia BounceEase.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="425a5-131">![Wykresy krzywych napięcia CircleEase.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="425a5-132">![Wykresy krzywych napięcia CubicEase.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="425a5-133">![ElasticEase z wykresami różnych easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="425a5-134">![ExponentialEase wykresy różnych easingmodesów.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="425a5-135">![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="425a5-136">![QuadraticEase z wykresami różnych easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="425a5-137">![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="425a5-138">![QuinticEase z wykresami różnych easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="425a5-139">![SineEase dla różnych wartości napięciamode](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="425a5-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="425a5-140">Można <xref:System.Windows.Media.Animation.PowerEase> użyć, aby utworzyć takie samo zachowanie jak <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase>, i <xref:System.Windows.Media.Animation.QuinticEase> przy użyciu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="425a5-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="425a5-141">Na przykład, jeśli chcesz użyć <xref:System.Windows.Media.Animation.PowerEase> do podstawiania dla <xref:System.Windows.Media.Animation.CubicEase>, określ <xref:System.Windows.Media.Animation.PowerEase.Power%2A> wartość 3.</span><span class="sxs-lookup"><span data-stu-id="425a5-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="425a5-142">Oprócz korzystania z funkcji krzywych napięcia zawartych w czasie wykonywania, można utworzyć własne niestandardowe funkcje napięcia, dziedzicząc z <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="425a5-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="425a5-143">Poniższy przykład ilustruje sposób tworzenia prostej niestandardowej funkcji napięcia.</span><span class="sxs-lookup"><span data-stu-id="425a5-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="425a5-144">Można dodać własną logikę matematyczną do zachowania funkcji krzywych napięcia, zastępując <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="425a5-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
