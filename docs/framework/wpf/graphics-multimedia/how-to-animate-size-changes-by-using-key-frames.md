---
title: Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0c2828215527a285943a79920de51fa42fe7a8a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559895"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych
W tym przykładzie przedstawiono sposób animowanie zmian rozmiaru przy użyciu klucza ramki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.ArcSegment.Size%2A> właściwość <xref:System.Windows.Media.ArcSegment>. Ta animacja używa trzech klatek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego pół sekundy animacji używa wystąpienia <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> klasy stopniowo zwiększać rozmiar łuku. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> utworzyć liniowej przejścia między wartościami.  
  
2.  Po zakończeniu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> klasy nagle zwiększyć rozmiar łuk. Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> utworzyć nagłym przechodzi między wartościami, oznacza to, zmiany rozmiaru wystąpić nagle i nie są niewielkie.  
  
3.  W ostatnim dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> klasę, aby zwiększyć rozmiar łuk. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> właściwości. W tym przykładzie rozmiar łuk powoli zwiększa się na początku i znacznie zwiększa, do końca segmentu czasu.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
