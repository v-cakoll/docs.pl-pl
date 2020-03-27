---
title: Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344652"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować zmiany rozmiaru przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.ArcSegment.Size%2A> klasy do <xref:System.Windows.Media.ArcSegment>animowania właściwości programu . Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:  
  
1. W pierwszej połowie drugiej części animacji, używa <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> wystąpienia klasy, aby stopniowo zwiększać rozmiar łuku. Liniowe klatki <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.  
  
2. Pod koniec następnej połowy drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> klasy, aby nagle zwiększyć rozmiar łuku. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami, oznacza to, że zmiany rozmiaru występują nagle i nie są subtelne.  
  
3. W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> wystąpienia klasy, aby zwiększyć rozmiar łuku. Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości. W tym przykładzie rozmiar łuku zwiększa się powoli na początku, a następnie zwiększa wykładniczo pod koniec segmentu czasu.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
