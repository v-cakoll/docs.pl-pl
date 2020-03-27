---
title: Jak animować kolor z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344747"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Jak animować kolor z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.SolidColorBrush> za pomocą klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.SolidColorBrush.Color%2A> klasy do <xref:System.Windows.Media.SolidColorBrush>animowania właściwości . . Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:  
  
1. W ciągu pierwszych dwóch sekund używa <xref:System.Windows.Media.Animation.LinearColorKeyFrame> wystąpienia klasy, aby stopniowo zmieniać kolor z zielonego na czerwony. Liniowe klatki <xref:System.Windows.Media.Animation.LinearColorKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.  
  
2. Pod koniec następnej połowy drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> klasy, aby szybko zmienić kolor z czerwonego na żółty. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> kluczowe, takie jak tworzenie nagłych zmian między wartościami, to znaczy, zmiana koloru w tej części animacji występuje szybko i nie jest subtelna.  
  
3. W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineColorKeyFrame> wystąpienia klasy, aby ponownie zmienić kolor — tym razem z żółtego z powrotem na zielony. Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineColorKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości. W tym przykładzie zmiana koloru rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
