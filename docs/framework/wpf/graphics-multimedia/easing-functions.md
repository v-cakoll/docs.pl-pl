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
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186499"
---
# <a name="easing-functions"></a><span data-ttu-id="8323b-102">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="8323b-102">Easing Functions</span></span>
<span data-ttu-id="8323b-103">Funkcje dynamiki umożliwiają stosowanie niestandardowych formuł matematycznych do animacji.</span><span class="sxs-lookup"><span data-stu-id="8323b-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="8323b-104">Na przykład możesz chcieć, aby obiekt realistycznie odbijał się lub zachowywał się tak, jakby znajdował się na sprężynie.</span><span class="sxs-lookup"><span data-stu-id="8323b-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="8323b-105">Można użyć key-frame lub nawet From / To / By animacje do przybliżenia tych efektów, ale zajęłoby znaczną ilość pracy i animacji będzie mniej dokładne niż przy użyciu formuły matematycznej.</span><span class="sxs-lookup"><span data-stu-id="8323b-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="8323b-106">Oprócz tworzenia własnej funkcji dynamiki niestandardowej przez dziedziczenie z programu , można użyć jednej z <xref:System.Windows.Media.Animation.EasingFunctionBase>kilku funkcji dynamiki dostarczonych przez środowisko uruchomieniowe, aby utworzyć typowe efekty.</span><span class="sxs-lookup"><span data-stu-id="8323b-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="8323b-107"><xref:System.Windows.Media.Animation.BackEase>: Cofa nieco ruch animacji, zanim zacznie się animować w wskazanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8323b-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="8323b-108"><xref:System.Windows.Media.Animation.BounceEase>: Tworzy efekt odbijania.</span><span class="sxs-lookup"><span data-stu-id="8323b-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="8323b-109"><xref:System.Windows.Media.Animation.CircleEase>: Tworzy animację, która przyspiesza i/lub zwalnia za pomocą funkcji kołowej.</span><span class="sxs-lookup"><span data-stu-id="8323b-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="8323b-110"><xref:System.Windows.Media.Animation.CubicEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="8323b-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="8323b-111"><xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animację, która przypomina sprężynę oscylacating tam iz powrotem, aż do odpoczynku.</span><span class="sxs-lookup"><span data-stu-id="8323b-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="8323b-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły wykładniczej.</span><span class="sxs-lookup"><span data-stu-id="8323b-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="8323b-113"><xref:System.Windows.Media.Animation.PowerEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>p,</sup> gdzie p jest równa <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8323b-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="8323b-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="8323b-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="8323b-115"><xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="8323b-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="8323b-116"><xref:System.Windows.Media.Animation.QuinticEase>: Utworzyć animację, która przyspiesza i/lub zwalnia za pomocą formuły *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="8323b-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="8323b-117"><xref:System.Windows.Media.Animation.SineEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły sinusoidańskiej.</span><span class="sxs-lookup"><span data-stu-id="8323b-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="8323b-118">Aby zastosować funkcję dynamiki do `EasingFunction` animacji, należy użyć właściwości animacji określić funkcję dynamiki, aby zastosować do animacji.</span><span class="sxs-lookup"><span data-stu-id="8323b-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="8323b-119">Poniższy przykład stosuje <xref:System.Windows.Media.Animation.BounceEase> funkcję dynamiki do a, <xref:System.Windows.Media.Animation.DoubleAnimation> aby utworzyć efekt odbijania.</span><span class="sxs-lookup"><span data-stu-id="8323b-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="8323b-120">W poprzednim przykładzie funkcja dynamiki została zastosowana do animacji Od/Do/Przez.</span><span class="sxs-lookup"><span data-stu-id="8323b-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="8323b-121">Te funkcje dynamiki można również zastosować do animacji klatki kluczowej.</span><span class="sxs-lookup"><span data-stu-id="8323b-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="8323b-122">W poniższym przykładzie pokazano, jak używać klatek kluczowych z funkcjami dynamiki skojarzonymi z nimi, aby utworzyć animację prostokąta, który kurczy się w górę, spowalnia, a następnie rozwija się w dół (jakby spada), a następnie odbija się do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="8323b-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="8323b-123">Za pomocą <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> właściwości można zmienić zachowanie funkcji dynamiki, czyli zmienić sposób interpolacji animacji.</span><span class="sxs-lookup"><span data-stu-id="8323b-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="8323b-124">Istnieją trzy możliwe wartości, <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>które można podać dla:</span><span class="sxs-lookup"><span data-stu-id="8323b-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="8323b-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacja jest zgodna z formułą matematyczną skojarzoną z funkcją dynamiki.</span><span class="sxs-lookup"><span data-stu-id="8323b-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="8323b-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacja następuje 100% interpolacji minus wyjście formuły związanej z funkcją dynamiki.</span><span class="sxs-lookup"><span data-stu-id="8323b-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="8323b-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolacja <xref:System.Windows.Media.Animation.EasingMode.EaseIn> wykorzystuje w pierwszej połowie <xref:System.Windows.Media.Animation.EasingMode.EaseOut> animacji i na drugą połowę.</span><span class="sxs-lookup"><span data-stu-id="8323b-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="8323b-128">Poniższe wykresy pokazują różne <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> wartości, gdzie *f*(*x*) reprezentuje postęp animacji i *t* reprezentuje czas.</span><span class="sxs-lookup"><span data-stu-id="8323b-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="8323b-129">![BackEase EasingMode wykresy.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="8323b-130">![BounceEase EasingMode wykresy.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="8323b-131">![Wykresy CircleEase EasingMode.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="8323b-132">![CubicEase EasingMode wykresy.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="8323b-133">![ElasticEase z wykresami różnych easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="8323b-134">![Wykładnicze Wykresy oazy różnych trybów easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="8323b-135">![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="8323b-136">![QuadraticEase z wykresami różnych easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="8323b-137">![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="8323b-138">![QuinticEase z wykresami różnych easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="8323b-139">![SineEase dla różnych wartości EasingMode](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8323b-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8323b-140">Można użyć <xref:System.Windows.Media.Animation.PowerEase> do utworzenia <xref:System.Windows.Media.Animation.CubicEase>tego <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase>samego <xref:System.Windows.Media.Animation.QuinticEase> zachowania co <xref:System.Windows.Media.Animation.PowerEase.Power%2A> , , i za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="8323b-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="8323b-141">Na przykład, jeśli chcesz <xref:System.Windows.Media.Animation.PowerEase> użyć <xref:System.Windows.Media.Animation.CubicEase>do zastąpienia <xref:System.Windows.Media.Animation.PowerEase.Power%2A> , określ wartość 3.</span><span class="sxs-lookup"><span data-stu-id="8323b-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="8323b-142">Oprócz korzystania z funkcji dynamiki zawartych w czasie wykonywania, można utworzyć własne <xref:System.Windows.Media.Animation.EasingFunctionBase>niestandardowe funkcje dynamiki, dziedzicząc po .</span><span class="sxs-lookup"><span data-stu-id="8323b-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="8323b-143">W poniższym przykładzie pokazano, jak utworzyć prostą niestandardową funkcję dynamiki.</span><span class="sxs-lookup"><span data-stu-id="8323b-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="8323b-144">Można dodać własną logikę matematyczną dla zachowania funkcji dynamiki, zastępując <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="8323b-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
