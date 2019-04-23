---
title: 'Instrukcje: Animowanie zmian rozmiaru przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0629b6600444bd172af451fd7e970bff894d8047
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342371"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Instrukcje: Animowanie zmian rozmiaru przy użyciu klatek kluczowych
Ten przykład pokazuje, jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.ArcSegment.Size%2A> właściwość <xref:System.Windows.Media.ArcSegment>. Ta animacja używa trzech ramek kluczowych w następujący sposób:  
  
1. Podczas pierwszego pół sekundy animacji używa wystąpienia <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> klasy, aby stopniowo zwiększać rozmiar łuku. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> utworzyć płynne przejście liniowy między wartościami.  
  
2. Na końcu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> klasy nagle zwiększyć rozmiar łuku. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, zmiany rozmiaru nagle występują i nie są subtelne.  
  
3. Za pośrednictwem końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> klasy, aby zwiększyć rozmiar łuku. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> właściwości. W tym przykładzie rozmiar łuk powoli zwiększa się na początku i wykładniczo zwiększa, kierunku końca odcinka czasu.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
