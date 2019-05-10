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
ms.openlocfilehash: a74142b8d8ee3a68daa9966e3f20f3b8e3becb72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615401"
---
# <a name="easing-functions"></a>Zwalnianie funkcji
Funkcji easingu umożliwiają zastosowanie niestandardowych wzory matematyczne do animacji. Na przykład może być obiekt realistycznie Odbijanie lub zachowują się tak, jakby był na platformy spring. Można użyć kluczowych klatek lub nawet od/do/przez animacji, które znajdują się obliczyć przybliżoną te skutki, ale zająć znaczną ilość pracy, a następnie animacji będzie mniej dokładnie niż przy użyciu formuły matematyczne.  
  
 Oprócz tworzenia własnych niestandardowych funkcji sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>, używasz jednej z kilku funkcji sterowania tempem zmian dostarczane przez środowisko uruchomieniowe do tworzenia efektów wspólnej.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Wycofuje nieco ruchu animacji, zanim rozpocznie się animować w wskazanej ścieżce.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Tworzy efekt odbijania.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu funkcji cykliczne.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Tworzy animacji podobny platformy spring Densytometr i z powrotem do momentu zakończenia rest.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu wykładniczego formuły.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>p</sup> gdzie p jest równa <xref:System.Windows.Media.Animation.PowerEase.Power%2A>właściwości.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Utworzyć animację, które przyspieszają i/lub zwalnia przy użyciu formuły *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Tworzy animacji, które przyspieszają i/lub zwalnia przy użyciu formuły sinus.  
  
 Aby zastosować funkcję przyspieszania do animacji, należy użyć `EasingFunction` właściwość animacji określać funkcję przyspieszania do zastosowania do animacji. Następujący przykład dotyczy <xref:System.Windows.Media.Animation.BounceEase> funkcja do przyspieszania <xref:System.Windows.Media.Animation.DoubleAnimation> utworzyć efekt odbijania.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 W poprzednim przykładzie zastosowano funkcję sterowania tempem zmian do od/do/przez animację. Tych funkcji sterowania tempem zmian można dotyczą również Animacja kluczowych klatek. Poniższy przykład pokazuje, jak za pomocą klatek kluczowych skojarzonych z nimi funkcje easingu utworzyć animację prostokąt, który kontraktów w górę, spowalnia, a następnie rozwija stawki rabatowe (tak, jakby objętych) i następnie odbija zostać zatrzymane.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Możesz użyć <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> właściwości do zmiany funkcji sterowania tempem zmian zachowania, oznacza to zmienić, jak interpolacji animacji. Istnieją trzy możliwe wartości, możesz nadać dla <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolacja następuje formuły matematyczne skojarzone z funkcji sterowania tempem zmian.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolacja poniżej 100% interpolacji minus dane wyjściowe formuły skojarzone z funkcji sterowania tempem zmian.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Zastosowań interpolacji <xref:System.Windows.Media.Animation.EasingMode.EaseIn> w pierwszej połowie animacji i <xref:System.Windows.Media.Animation.EasingMode.EaseOut> przez drugą połowę.  
  
 Poniższe wykresy pokazują różne wartości <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> gdzie *f*(*x*) reprezentuje postęp animacji i *t* reprezentuje czas.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Wykresy obiektu BackEase w trybie. ](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Wykresy obiektu BounceEase w trybie. ](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Wykresy obiektu CircleEase w trybie. ](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Wykresy obiektu CubicEase w trybie. ](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![Obiekt ElasticEase wykresów dla różnych trybów EasingMode. ](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Obiekt ExponentialEase wykresy dla różnych trybów EasingMode. ](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![Obiekt QuarticEase wykresów dla różnych trybów EasingMode. ](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Obiekt QuadraticEase wykresów dla różnych trybów EasingMode](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![Obiekt QuarticEase wykresów dla różnych trybów EasingMode. ](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Obiekt QuinticEase wykresów dla różnych trybów EasingMode. ](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase dla różnych wartości obiektu](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Możesz użyć <xref:System.Windows.Media.Animation.PowerEase> takie samo zachowanie, jak utworzyć <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, i <xref:System.Windows.Media.Animation.QuinticEase> przy użyciu <xref:System.Windows.Media.Animation.PowerEase.Power%2A> właściwości. Na przykład, jeśli chcesz użyć <xref:System.Windows.Media.Animation.PowerEase> do podstawienia w <xref:System.Windows.Media.Animation.CubicEase>, określ <xref:System.Windows.Media.Animation.PowerEase.Power%2A> wartość 3.  
  
 Oprócz używania funkcji easingu zawarte w czasie wykonywania, można utworzyć własne niestandardowe funkcje sterowania tempem zmian przez dziedziczenie z <xref:System.Windows.Media.Animation.EasingFunctionBase>. Poniższy przykład przedstawia sposób tworzenia prostej niestandardowych funkcji sterowania tempem zmian. Można dodać własną logiką matematyczne do zachowania funkcji sterowania tempem zmian przez zastąpienie <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> metody.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
