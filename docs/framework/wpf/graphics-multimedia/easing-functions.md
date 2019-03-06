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
ms.openlocfilehash: 456308e37bddc1df86b49085139a3810c4959a58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354508"
---
# <a name="easing-functions"></a><span data-ttu-id="851fc-102">Zwalnianie funkcji</span><span class="sxs-lookup"><span data-stu-id="851fc-102">Easing Functions</span></span>
<span data-ttu-id="851fc-103">Funkcji easingu umożliwiają zastosowanie niestandardowych wzory matematyczne do animacji.</span><span class="sxs-lookup"><span data-stu-id="851fc-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="851fc-104">Na przykład może być obiekt realistycznie Odbijanie lub zachowują się tak, jakby był na platformy spring.</span><span class="sxs-lookup"><span data-stu-id="851fc-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="851fc-105">Można użyć kluczowych klatek lub nawet od/do/przez animacji, które znajdują się obliczyć przybliżoną te skutki, ale zająć znaczną ilość pracy, a następnie animacji będzie mniej dokładnie niż przy użyciu formuły matematyczne.</span><span class="sxs-lookup"><span data-stu-id="851fc-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="851fc-106">Oprócz tworzenia własnych niestandardowych funkcji sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>, używasz jednej z kilku funkcji sterowania tempem zmian dostarczane przez środowisko uruchomieniowe do tworzenia efektów wspólnej.</span><span class="sxs-lookup"><span data-stu-id="851fc-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="851fc-107"><xref:System.Windows.Media.Animation.BackEase>: Wycofuje nieco ruchu animacji, zanim rozpocznie się animować w wskazanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="851fc-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="851fc-108"><xref:System.Windows.Media.Animation.BounceEase>: Tworzy efekt odbijania.</span><span class="sxs-lookup"><span data-stu-id="851fc-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="851fc-109"><xref:System.Windows.Media.Animation.CircleEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu funkcji cykliczne.</span><span class="sxs-lookup"><span data-stu-id="851fc-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="851fc-110"><xref:System.Windows.Media.Animation.CubicEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="851fc-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="851fc-111"><xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animacji podobny platformy spring Densytometr i z powrotem do momentu zakończenia rest.</span><span class="sxs-lookup"><span data-stu-id="851fc-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="851fc-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu wykładniczego formuły.</span><span class="sxs-lookup"><span data-stu-id="851fc-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="851fc-113"><xref:System.Windows.Media.Animation.PowerEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>p</sup> gdzie p jest równa <xref:System.Windows.Media.Animation.PowerEase.Power%2A>właściwości.</span><span class="sxs-lookup"><span data-stu-id="851fc-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="851fc-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="851fc-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="851fc-115"><xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="851fc-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="851fc-116"><xref:System.Windows.Media.Animation.QuinticEase>: Utworzyć animację, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="851fc-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="851fc-117"><xref:System.Windows.Media.Animation.SineEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły sinus.</span><span class="sxs-lookup"><span data-stu-id="851fc-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="851fc-118">Aby zastosować funkcję przyspieszania do animacji, należy użyć `EasingFunction` właściwość animacji określać funkcję przyspieszania do zastosowania do animacji.</span><span class="sxs-lookup"><span data-stu-id="851fc-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="851fc-119">Następujący przykład dotyczy <xref:System.Windows.Media.Animation.BounceEase> funkcja do przyspieszania <xref:System.Windows.Media.Animation.DoubleAnimation> utworzyć efekt odbijania.</span><span class="sxs-lookup"><span data-stu-id="851fc-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="851fc-120">W poprzednim przykładzie zastosowano funkcję sterowania tempem zmian do od/do/przez animację.</span><span class="sxs-lookup"><span data-stu-id="851fc-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="851fc-121">Tych funkcji sterowania tempem zmian można dotyczą również Animacja kluczowych klatek.</span><span class="sxs-lookup"><span data-stu-id="851fc-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="851fc-122">Poniższy przykład pokazuje, jak za pomocą klatek kluczowych skojarzonych z nimi funkcje easingu utworzyć animację prostokąt, który kontraktów w górę, spowalnia, a następnie rozwija stawki rabatowe (tak, jakby objętych) i następnie odbija zostać zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="851fc-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="851fc-123">Możesz użyć <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> właściwości do zmiany funkcji sterowania tempem zmian zachowania, oznacza to zmienić, jak interpolacji animacji.</span><span class="sxs-lookup"><span data-stu-id="851fc-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="851fc-124">Istnieją trzy możliwe wartości, możesz nadać dla <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="851fc-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="851fc-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacja następuje formuły matematyczne skojarzone z funkcji sterowania tempem zmian.</span><span class="sxs-lookup"><span data-stu-id="851fc-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="851fc-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacja poniżej 100% interpolacji minus dane wyjściowe formuły skojarzone z funkcji sterowania tempem zmian.</span><span class="sxs-lookup"><span data-stu-id="851fc-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="851fc-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Zastosowań interpolacji <xref:System.Windows.Media.Animation.EasingMode.EaseIn> w pierwszej połowie animacji i <xref:System.Windows.Media.Animation.EasingMode.EaseOut> przez drugą połowę.</span><span class="sxs-lookup"><span data-stu-id="851fc-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="851fc-128">Poniższe wykresy pokazują różne wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> gdzie *f*(*x*) reprezentuje postęp animacji i *t* reprezentuje czas.</span><span class="sxs-lookup"><span data-stu-id="851fc-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="851fc-129">![Wykresy obiektu BackEase w trybie. ](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="851fc-130">![Wykresy obiektu BounceEase w trybie. ](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="851fc-131">![Wykresy obiektu CircleEase w trybie. ](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="851fc-132">![Wykresy obiektu CubicEase w trybie. ](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="851fc-133">![Obiekt ElasticEase wykresów dla różnych trybów EasingMode. ](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="851fc-134">![Obiekt ExponentialEase wykresy dla różnych trybów EasingMode. ](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="851fc-135">![Obiekt QuarticEase wykresów dla różnych trybów EasingMode. ](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="851fc-136">![Obiekt QuadraticEase wykresów dla różnych trybów EasingMode](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="851fc-137">![Obiekt QuarticEase wykresów dla różnych trybów EasingMode. ](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="851fc-138">![Obiekt QuinticEase wykresów dla różnych trybów EasingMode. ](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="851fc-139">![SineEase dla różnych wartości obiektu](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="851fc-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="851fc-140">Możesz użyć <xref:System.Windows.Media.Animation.PowerEase> takie samo zachowanie, jak utworzyć <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, i <xref:System.Windows.Media.Animation.QuinticEase> przy użyciu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="851fc-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="851fc-141">Na przykład, jeśli chcesz użyć <xref:System.Windows.Media.Animation.PowerEase> do podstawienia w <xref:System.Windows.Media.Animation.CubicEase>, określ <xref:System.Windows.Media.Animation.PowerEase.Power%2A> wartość 3.</span><span class="sxs-lookup"><span data-stu-id="851fc-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="851fc-142">Oprócz używania funkcji easingu zawarte w czasie wykonywania, można utworzyć własne niestandardowe funkcje sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="851fc-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="851fc-143">Poniższy przykład przedstawia sposób tworzenia prostej niestandardowych funkcji sterowania tempem zmian.</span><span class="sxs-lookup"><span data-stu-id="851fc-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="851fc-144">Można dodać własną logiką matematyczne do zachowania funkcji sterowania tempem zmian przez zastąpienie <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="851fc-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
