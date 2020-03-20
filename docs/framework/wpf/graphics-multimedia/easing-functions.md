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
# <a name="easing-functions"></a>Zwalnianie funkcji
Funkcje dynamiki umożliwiają stosowanie niestandardowych formuł matematycznych do animacji. Na przykład możesz chcieć, aby obiekt realistycznie odbijał się lub zachowywał się tak, jakby znajdował się na sprężynie. Można użyć key-frame lub nawet From / To / By animacje do przybliżenia tych efektów, ale zajęłoby znaczną ilość pracy i animacji będzie mniej dokładne niż przy użyciu formuły matematycznej.  
  
 Oprócz tworzenia własnej funkcji dynamiki niestandardowej przez dziedziczenie z programu , można użyć jednej z <xref:System.Windows.Media.Animation.EasingFunctionBase>kilku funkcji dynamiki dostarczonych przez środowisko uruchomieniowe, aby utworzyć typowe efekty.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Cofa nieco ruch animacji, zanim zacznie się animować w wskazanej ścieżce.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Tworzy efekt odbijania.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Tworzy animację, która przyspiesza i/lub zwalnia za pomocą funkcji kołowej.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animację, która przypomina sprężynę oscylacating tam iz powrotem, aż do odpoczynku.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły wykładniczej.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>p,</sup> gdzie p jest równa <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Utworzyć animację, która przyspiesza i/lub zwalnia za pomocą formuły *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Tworzy animację, która przyspiesza i/lub zwalnia przy użyciu formuły sinusoidańskiej.  
  
 Aby zastosować funkcję dynamiki do `EasingFunction` animacji, należy użyć właściwości animacji określić funkcję dynamiki, aby zastosować do animacji. Poniższy przykład stosuje <xref:System.Windows.Media.Animation.BounceEase> funkcję dynamiki do a, <xref:System.Windows.Media.Animation.DoubleAnimation> aby utworzyć efekt odbijania.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 W poprzednim przykładzie funkcja dynamiki została zastosowana do animacji Od/Do/Przez. Te funkcje dynamiki można również zastosować do animacji klatki kluczowej. W poniższym przykładzie pokazano, jak używać klatek kluczowych z funkcjami dynamiki skojarzonymi z nimi, aby utworzyć animację prostokąta, który kurczy się w górę, spowalnia, a następnie rozwija się w dół (jakby spada), a następnie odbija się do zatrzymania.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Za pomocą <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> właściwości można zmienić zachowanie funkcji dynamiki, czyli zmienić sposób interpolacji animacji. Istnieją trzy możliwe wartości, <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>które można podać dla:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacja jest zgodna z formułą matematyczną skojarzoną z funkcją dynamiki.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacja następuje 100% interpolacji minus wyjście formuły związanej z funkcją dynamiki.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolacja <xref:System.Windows.Media.Animation.EasingMode.EaseIn> wykorzystuje w pierwszej połowie <xref:System.Windows.Media.Animation.EasingMode.EaseOut> animacji i na drugą połowę.  
  
 Poniższe wykresy pokazują różne <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> wartości, gdzie *f*(*x*) reprezentuje postęp animacji i *t* reprezentuje czas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode wykresy.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode wykresy.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Wykresy CircleEase EasingMode.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode wykresy.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase z wykresami różnych easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Wykładnicze Wykresy oazy różnych trybów easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase z wykresami różnych easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase z wykresami różnych easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase z wykresami różnych easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase dla różnych wartości EasingMode](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Można użyć <xref:System.Windows.Media.Animation.PowerEase> do utworzenia <xref:System.Windows.Media.Animation.CubicEase>tego <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase>samego <xref:System.Windows.Media.Animation.QuinticEase> zachowania co <xref:System.Windows.Media.Animation.PowerEase.Power%2A> , , i za pomocą właściwości. Na przykład, jeśli chcesz <xref:System.Windows.Media.Animation.PowerEase> użyć <xref:System.Windows.Media.Animation.CubicEase>do zastąpienia <xref:System.Windows.Media.Animation.PowerEase.Power%2A> , określ wartość 3.  
  
 Oprócz korzystania z funkcji dynamiki zawartych w czasie wykonywania, można utworzyć własne <xref:System.Windows.Media.Animation.EasingFunctionBase>niestandardowe funkcje dynamiki, dziedzicząc po . W poniższym przykładzie pokazano, jak utworzyć prostą niestandardową funkcję dynamiki. Można dodać własną logikę matematyczną dla zachowania funkcji dynamiki, zastępując <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metodę.
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
