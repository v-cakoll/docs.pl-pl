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
ms.openlocfilehash: 4adeb858ab1b69ef1b00f7bf3b6868dbcbbc4154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Jak animować double z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak można animować właściwości, która przyjmuje wartość <xref:System.Double> przy użyciu klucza ramki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład porusza się prostokąt na ekranie. W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> stosowane do <xref:System.Windows.Shapes.Rectangle>. Animacja powtarza nieskończoność, używa trzech klatek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego trzy sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> klasę, aby przenieść prostokąt na ścieżce stałą szybkością z punktu początkowego do 500 pozycji. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> utworzyć liniowej przejścia między wartościami.  
  
2.  Na końcu czwarty drugi używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> klasy nagle przesuwać pozycji dalej. Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> tworzenie nagłym przeskoków między wartościami. W tym przykładzie prostokąta znajduje się na pozycji początkowej i nagle pojawia się na 500 pozycji.  
  
3.  W ostatnim dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> klasę, aby przenieść prostokąt z powrotem do punktu początkowego. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartością <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> właściwości. W tym przykładzie prostokąt rozpoczyna się powoli przenosząc, a następnie przyspiesza wykładniczo do końca segmentu czasu.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Spójności z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt do zastosowania <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternatywnie podczas stosowania pojedynczego animacji w kodzie, łatwiej jest użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>. Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
