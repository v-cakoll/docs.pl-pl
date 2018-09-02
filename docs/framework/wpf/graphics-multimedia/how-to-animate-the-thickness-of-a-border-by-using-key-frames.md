---
title: Jak animować grubość obramowania z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: a601fd6779a4d912166366652435aff9ae37613f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421413"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Jak animować grubość obramowania z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>. Ta animacja używa trzech ramek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego pół sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> klasy, aby stopniowo zwiększać grubość obramowania. W przykładzie użyto <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> utworzyć smooth liniowy wzrost między wartościami.  
  
2.  Na końcu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> klasy nagłe zwiększenie grubość obramowania. Dyskretnych klatek kluczowych, takich jak te pochodzące z <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, jerky przepływu animacji.  
  
3.  Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> klasy, aby zmniejszyć grubość obramowania. Ramek kluczowych krzywej składanej, takich jak te pochodzące z <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> właściwości. W tym klatek kluczowych animacji wolno rozpoczyna się i przyspiesza wykładniczo w kierunku końca odcinka czasu.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Animowanie wartości BorderThickness](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
