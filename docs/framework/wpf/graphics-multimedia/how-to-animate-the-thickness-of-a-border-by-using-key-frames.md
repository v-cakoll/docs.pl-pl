---
title: Jak animować grubość obramowania z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344689"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Jak animować grubość obramowania z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość programu <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> użyto <xref:System.Windows.Controls.Control.BorderThickness%2A> klasy do <xref:System.Windows.Controls.Border>animowania właściwości . . Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:  
  
1. W pierwszej połowie drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> klasy, aby stopniowo zwiększać grubość granicy. W przykładzie <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> użyto do utworzenia płynnego wzrostu liniowego między wartościami.  
  
2. Pod koniec następnej połowy drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> klasy, aby nagle zwiększyć grubość obramowania. Dyskretne klatki kluczowe, takie <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> jak te pochodzące z tworzenia nagłych przeskoków między wartościami, to znaczy, że ruch animacji jest szarpany.  
  
3. W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> wystąpienia klasy, aby zmniejszyć grubość obramowania. Klatki kluczowe splajnu, takie jak te pochodzące <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> z <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> tworzenia zmiennego przejścia między wartościami zgodnie z wartościami właściwości. W tej klatce kluczowej animacja rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
- [Animowanie wartości BorderThickness](../controls/how-to-animate-a-borderthickness-value.md)
