---
title: Jak animować double z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 67466bbb5fd7e7a46c312e14666c23048bf43d80
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552260"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Jak animować double z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować wartość właściwości, która przyjmuje <xref:System.Double> przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje przeniesienie prostokąt na ekranie. W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> dotyczą <xref:System.Windows.Shapes.Rectangle>. Animacja jest powtarzany na czas nieokreślony, używa trzech ramek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego trzy sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> klasy, aby przenieść prostokąt na ścieżce według stałej stawki z punktu początkowego do 500 pozycji. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> utworzyć płynne przejście liniowy między wartościami.  
  
2.  Na koniec czwarte sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> klasy nagle przenieść prostokąt na pozycji dalej. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> tworzenie nagłe skoki między wartościami. W tym przykładzie prostokąta znajduje się na pozycji początkowej i następnie nagle pojawia się na 500 pozycji.  
  
3.  W ostatnim dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> klasy, aby przenieść prostokąt z powrotem do jego pozycja początkowa. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartością <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> właściwości. W tym przykładzie rozpoczyna się powoli przenosząc i następnie przyspiesza wykładniczo w kierunku końca odcinka czasu.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Aby zachować spójność z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt, aby zastosować <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternatywnie, stosując jednej animacji w kodzie, jest łatwiejszy w obsłudze <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
