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
# <a name="easing-functions"></a>Zwalnianie funkcji
Funkcje krzywych napięcia umożliwiają stosowanie niestandardowych formuł matematycznych do animacji. Na przykład, możesz chcieć, aby obiekt mógł odbijać lub zachowywać się tak, jakby był on sprężyną. Możesz użyć klatek kluczowych lub nawet z/do/przez animacje, aby przybliżyć te efekty, ale zajmiemy się znaczną ilością pracy, a animacja byłaby mniej dokładna niż użycie formuły matematycznej.  
  
 Oprócz tworzenia własnej niestandardowej funkcji napięcia przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>, można użyć jednej z kilku funkcji sterowania zapewnianego przez środowisko uruchomieniowe w celu utworzenia typowych efektów.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Wycofuje ruch animacji nieco przed rozpoczęciem animacji w wskazanej ścieżce.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Tworzy efekt odbijania.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu funkcji cyklicznej.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animację, która przypomina sprężynę z powrotem i do przodu, aż do momentu zapełnienia.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły wykładniczej.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>p</sup> , <xref:System.Windows.Media.Animation.PowerEase.Power%2A> gdzie p jest równe właściwości.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Utwórz animację, która przyspiesza i/lub chwyci przy użyciu formuły *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Tworzy animację, która przyspiesza i/lub chwyci przy użyciu formuły sinusa.  
  
 Aby zastosować funkcję krzywej napięcia do animacji, użyj `EasingFunction` właściwości animacji Określ funkcję krzywych napięcia, która ma zostać zastosowana do animacji. Poniższy przykład stosuje <xref:System.Windows.Media.Animation.BounceEase> funkcję krzywej napięcia do, <xref:System.Windows.Media.Animation.DoubleAnimation> aby utworzyć efekt odbijania.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 W poprzednim przykładzie funkcja napięcia została zastosowana do animacji z/do/przez. Można również zastosować te funkcje napięcia do animacji klatek kluczowych. Poniższy przykład pokazuje, jak używać klatek kluczowych z funkcją krzywych napięcia skojarzonych z nimi w celu utworzenia animacji prostokąta, który zawiera kontrakty w górę, spowalnia działanie, a następnie rozwija w dół (w przypadku spadku), a następnie odbija do zatrzymania.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Można użyć <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> właściwości, aby zmienić sposób zachowania funkcji krzywej napięcia, czyli zmienić sposób interpolacji animacji. Dostępne są trzy możliwe wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacja następuje po formule matematycznej skojarzonej z funkcją krzywych napięcia.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacja następuje po 100% interpolacji minus wynik formuły skojarzonej z funkcją krzywej napięcia.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolacja stosuje <xref:System.Windows.Media.Animation.EasingMode.EaseIn> się w pierwszej połowie animacji, a <xref:System.Windows.Media.Animation.EasingMode.EaseOut> druga połowa.  
  
 Poniższe wykresy przedstawiają różne wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> , gdzie *f*(*x*) reprezentuje postęp animacji, a czas .  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Wykresy] krzywych napięcia (./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Wykresy krzywych napięcia BounceEase.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Wykresy krzywych napięcia CircleEase.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Wykresy krzywych napięcia CubicEase.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase z wykresami różnych easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![ExponentialEase wykresy różnych easingmodesów.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase z wykresami różnych easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase z wykresami różnych easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase dla różnych wartości napięciamode](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Można <xref:System.Windows.Media.Animation.PowerEase> użyć, aby utworzyć takie samo zachowanie jak <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase>, i <xref:System.Windows.Media.Animation.QuinticEase> przy użyciu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości. Na przykład, jeśli chcesz użyć <xref:System.Windows.Media.Animation.PowerEase> do podstawiania dla <xref:System.Windows.Media.Animation.CubicEase>, określ <xref:System.Windows.Media.Animation.PowerEase.Power%2A> wartość 3.  
  
 Oprócz korzystania z funkcji krzywych napięcia zawartych w czasie wykonywania, można utworzyć własne niestandardowe funkcje napięcia, dziedzicząc z <xref:System.Windows.Media.Animation.EasingFunctionBase>. Poniższy przykład ilustruje sposób tworzenia prostej niestandardowej funkcji napięcia. Można dodać własną logikę matematyczną do zachowania funkcji krzywych napięcia, zastępując <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metodę.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
