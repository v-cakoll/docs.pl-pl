---
title: 'Instrukcje: Animuj kolor z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8d7dbe70f25b4712d1384a751a02053fb7f287ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645096"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Instrukcje: Animuj kolor z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush>. Ta animacja używa trzech ramek kluczowych w następujący sposób:  
  
1.  Podczas pierwszych dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.LinearColorKeyFrame> klasy, aby stopniowo kolor z zielonego do czerwonego. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearColorKeyFrame> utworzyć płynne przejście liniowy między wartościami.  
  
2.  Podczas koniec następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> klasy, aby szybko zmienić kolor czerwony na żółto. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> tworzenie nagłe zmiany między wartościami, to znaczy, zmiana koloru w tej części animacji odbywa się szybko, a nie subtelne.  
  
3.  Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineColorKeyFrame> klasy, aby zmienić kolor ponownie — tym razem z żółtym kopii na zielony. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineColorKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> właściwości. W tym przykładzie zmiana koloru rozpocznie się powoli i przyspiesza wykładniczo w kierunku końca odcinka czasu.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
