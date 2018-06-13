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
ms.openlocfilehash: 3ce7c1824dc53c154ba1091ea62c1b8950b757c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557566"
---
# <a name="easing-functions"></a><span data-ttu-id="16331-102">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="16331-102">Easing Functions</span></span>
<span data-ttu-id="16331-103">Funkcji sterowania tempem zmian umożliwiają stosowanie niestandardowych matematycznymi do animacji.</span><span class="sxs-lookup"><span data-stu-id="16331-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="16331-104">Na przykład możesz obiektu realistycznie Odbijanie lub zachowują się tak, jakby była na źródła.</span><span class="sxs-lookup"><span data-stu-id="16331-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="16331-105">Można użyć do przybliżonego określenia tych skutków ramki klucza lub nawet z lub do/przez animacje, ale zajmuje dużo pracy, a następnie animacji będzie dokładności mniejszej niż przy użyciu formuły matematycznych.</span><span class="sxs-lookup"><span data-stu-id="16331-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="16331-106">Oprócz tworzenia własnej niestandardowej funkcji sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>, można użyć jednej z kilku funkcji sterowania tempem zmian dostarczonym w czasie wykonywania można utworzyć typowe skutki.</span><span class="sxs-lookup"><span data-stu-id="16331-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="16331-107"><xref:System.Windows.Media.Animation.BackEase>: Wycofuje ruchu animacji nieco przed rozpoczęciem animacji w wskazanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="16331-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="16331-108"><xref:System.Windows.Media.Animation.BounceEase>: Efekt podskakujące tworzy.</span><span class="sxs-lookup"><span data-stu-id="16331-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="16331-109"><xref:System.Windows.Media.Animation.CircleEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu funkcji cyklicznej.</span><span class="sxs-lookup"><span data-stu-id="16331-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="16331-110"><xref:System.Windows.Media.Animation.CubicEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="16331-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="16331-111"><xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animacji podobny sprężynowy Densytometr i z powrotem do momentu zakończenia rest.</span><span class="sxs-lookup"><span data-stu-id="16331-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="16331-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły wykładniczej.</span><span class="sxs-lookup"><span data-stu-id="16331-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="16331-113"><xref:System.Windows.Media.Animation.PowerEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>p</sup> gdzie p jest równa <xref:System.Windows.Media.Animation.PowerEase.Power%2A>właściwości.</span><span class="sxs-lookup"><span data-stu-id="16331-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="16331-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="16331-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="16331-115"><xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="16331-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="16331-116"><xref:System.Windows.Media.Animation.QuinticEase>: Tworzenie animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="16331-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="16331-117"><xref:System.Windows.Media.Animation.SineEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły sinus.</span><span class="sxs-lookup"><span data-stu-id="16331-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="16331-118">Można sprawdzić działanie tych funkcji sterowania tempem zmian z następującym przykładowym.</span><span class="sxs-lookup"><span data-stu-id="16331-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="16331-119">Uruchomienie tego przykładu</span><span class="sxs-lookup"><span data-stu-id="16331-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="16331-120">Aby zastosować funkcji sterowania tempem zmian do animacji, użyj `EasingFunction` właściwości animacji Określ funkcji sterowania tempem zmian do zastosowania do animacji.</span><span class="sxs-lookup"><span data-stu-id="16331-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="16331-121">Następujący przykład dotyczy <xref:System.Windows.Media.Animation.BounceEase> łatwiejszym funkcji <xref:System.Windows.Media.Animation.DoubleAnimation> utworzyć podskakujące efekt.</span><span class="sxs-lookup"><span data-stu-id="16331-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="16331-122">Uruchomienie tego przykładu</span><span class="sxs-lookup"><span data-stu-id="16331-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="16331-123">W poprzednim przykładzie funkcji sterowania tempem zmian została zastosowana do From lub do/przez animacji.</span><span class="sxs-lookup"><span data-stu-id="16331-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="16331-124">Tych funkcji sterowania tempem zmian może dotyczyć również klucza ramki animacji.</span><span class="sxs-lookup"><span data-stu-id="16331-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="16331-125">Poniższy przykład przedstawia użycie klatek kluczowych napięcia skojarzonych z nimi funkcje, aby utworzyć animację prostokąt kontraktów w górę, spowalnia, a następnie rozwijane w dół (tak, jakby objętych) i następnie odrzuceń do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="16331-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="16331-126">Uruchomienie tego przykładu</span><span class="sxs-lookup"><span data-stu-id="16331-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="16331-127">Można użyć <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> zmienić właściwości do zmiany funkcji sterowania tempem zmian zachowania, oznacza to, jak interpolacji animacji.</span><span class="sxs-lookup"><span data-stu-id="16331-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="16331-128">Istnieją trzy możliwe wartości można nadać dla <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="16331-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="16331-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacji następuje formuła matematyczna skojarzone z funkcji sterowania tempem zmian.</span><span class="sxs-lookup"><span data-stu-id="16331-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="16331-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacji następuje interpolacji 100% minus dane wyjściowe formuły skojarzone z funkcji sterowania tempem zmian.</span><span class="sxs-lookup"><span data-stu-id="16331-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="16331-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Używa interpolacji <xref:System.Windows.Media.Animation.EasingMode.EaseIn> dla pierwszej połowy animacji i <xref:System.Windows.Media.Animation.EasingMode.EaseOut> dla drugiej połowie tematu.</span><span class="sxs-lookup"><span data-stu-id="16331-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="16331-132">Wykresy poniżej pokazują różne wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> gdzie *f*(*x*) reprezentuje postęp animacji i *t* reprezentuje czas.</span><span class="sxs-lookup"><span data-stu-id="16331-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="16331-133">![Wykresy obiektu BackEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="16331-134">![Wykresy obiektu BounceEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="16331-135">![Wykresy obiektu CircleEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="16331-136">![Wykresy obiektu CubicEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="16331-137">![Obiekt ElasticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="16331-138">![Wykresy obiektu ExponentialEase dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="16331-139">![Obiekt QuarticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="16331-140">![Obiekt QuadraticEase wykresy dla różnych trybów EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="16331-141">![Obiekt QuarticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="16331-142">![Obiekt QuinticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="16331-143">![SineEase dla różnych wartości obiektu](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="16331-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16331-144">Można użyć <xref:System.Windows.Media.Animation.PowerEase> można utworzyć zachowania <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, i <xref:System.Windows.Media.Animation.QuinticEase> przy użyciu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="16331-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="16331-145">Na przykład, jeśli chcesz użyć <xref:System.Windows.Media.Animation.PowerEase> do zastąpienia dla <xref:System.Windows.Media.Animation.CubicEase>, określ <xref:System.Windows.Media.Animation.PowerEase.Power%2A> wartość 3.</span><span class="sxs-lookup"><span data-stu-id="16331-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="16331-146">Oprócz przy użyciu funkcji sterowania tempem zmian, zawarte w czasie wykonywania, można tworzyć własne niestandardowe funkcji sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="16331-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="16331-147">Poniższy przykład przedstawia sposób tworzenia prostego niestandardowej funkcji sterowania tempem zmian.</span><span class="sxs-lookup"><span data-stu-id="16331-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="16331-148">Można dodać własną logikę matematyczną dla zachowania funkcji sterowania tempem zmian przez zastąpienie <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="16331-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="16331-149">Uruchomienie tego przykładu</span><span class="sxs-lookup"><span data-stu-id="16331-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
