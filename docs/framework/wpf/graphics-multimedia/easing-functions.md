---
title: Zwalnianie funkcji
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 570a065d3f28befe8db4887ff908c3bd60a639a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="easing-functions"></a>Zwalnianie funkcji
Funkcji sterowania tempem zmian umożliwiają stosowanie niestandardowych matematycznymi do animacji. Na przykład możesz obiektu realistycznie Odbijanie lub zachowują się tak, jakby była na źródła. Można użyć do przybliżonego określenia tych skutków ramki klucza lub nawet z lub do/przez animacje, ale zajmuje dużo pracy, a następnie animacji będzie dokładności mniejszej niż przy użyciu formuły matematycznych.  
  
 Oprócz tworzenia własnej niestandardowej funkcji sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>, można użyć jednej z kilku funkcji sterowania tempem zmian dostarczonym w czasie wykonywania można utworzyć typowe skutki.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: Wycofuje ruchu animacji nieco przed rozpoczęciem animacji w wskazanej ścieżce.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: Efekt podskakujące tworzy.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu funkcji cyklicznej.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animacji podobny sprężynowy Densytometr i z powrotem do momentu zakończenia rest.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły wykładniczej.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>p</sup> gdzie p jest równa <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: Tworzenie animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły sinus.  
  
 Można sprawdzić działanie tych funkcji sterowania tempem zmian z następującym przykładowym.  
  
 [Uruchomienie tego przykładu](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 Aby zastosować funkcji sterowania tempem zmian do animacji, użyj `EasingFunction` właściwości animacji Określ funkcji sterowania tempem zmian do zastosowania do animacji. Następujący przykład dotyczy <xref:System.Windows.Media.Animation.BounceEase> łatwiejszym funkcji <xref:System.Windows.Media.Animation.DoubleAnimation> utworzyć podskakujące efekt.  
  
 [Uruchomienie tego przykładu](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 W poprzednim przykładzie funkcji sterowania tempem zmian została zastosowana do From lub do/przez animacji. Tych funkcji sterowania tempem zmian może dotyczyć również klucza ramki animacji. Poniższy przykład przedstawia użycie klatek kluczowych napięcia skojarzonych z nimi funkcje, aby utworzyć animację prostokąt kontraktów w górę, spowalnia, a następnie rozwijane w dół (tak, jakby objętych) i następnie odrzuceń do zatrzymania.  
  
 [Uruchomienie tego przykładu](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Można użyć <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> zmienić właściwości do zmiany funkcji sterowania tempem zmian zachowania, oznacza to, jak interpolacji animacji. Istnieją trzy możliwe wartości można nadać dla <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacji następuje formuła matematyczna skojarzone z funkcji sterowania tempem zmian.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacji następuje interpolacji 100% minus dane wyjściowe formuły skojarzone z funkcji sterowania tempem zmian.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Używa interpolacji <xref:System.Windows.Media.Animation.EasingMode.EaseIn> dla pierwszej połowy animacji i <xref:System.Windows.Media.Animation.EasingMode.EaseOut> dla drugiej połowie tematu.  
  
 Wykresy poniżej pokazują różne wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> gdzie *f*(*x*) reprezentuje postęp animacji i *t* reprezentuje czas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Wykresy obiektu BackEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Wykresy obiektu BounceEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Wykresy obiektu CircleEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Wykresy obiektu CubicEase w trybie. ] (../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![Obiekt ElasticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Wykresy obiektu ExponentialEase dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![Obiekt QuarticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Obiekt QuadraticEase wykresy dla różnych trybów EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![Obiekt QuarticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Obiekt QuinticEase wykresy dla różnych trybów EasingMode. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase dla różnych wartości obiektu](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Można użyć <xref:System.Windows.Media.Animation.PowerEase> można utworzyć zachowania <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, i <xref:System.Windows.Media.Animation.QuinticEase> przy użyciu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości. Na przykład, jeśli chcesz użyć <xref:System.Windows.Media.Animation.PowerEase> do zastąpienia dla <xref:System.Windows.Media.Animation.CubicEase>, określ <xref:System.Windows.Media.Animation.PowerEase.Power%2A> wartość 3.  
  
 Oprócz przy użyciu funkcji sterowania tempem zmian, zawarte w czasie wykonywania, można tworzyć własne niestandardowe funkcji sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>. Poniższy przykład przedstawia sposób tworzenia prostego niestandardowej funkcji sterowania tempem zmian. Można dodać własną logikę matematyczną dla zachowania funkcji sterowania tempem zmian przez zastąpienie <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody.  
  
 [Uruchomienie tego przykładu](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
