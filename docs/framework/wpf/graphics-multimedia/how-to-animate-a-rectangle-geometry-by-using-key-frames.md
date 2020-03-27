---
title: Jak animować geometrię prostokąta z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344678"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Jak animować geometrię prostokąta z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.RectangleGeometry.Rect%2A> właściwość a <xref:System.Windows.Media.RectangleGeometry> za pomocą klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.RectangleGeometry.Rect%2A> klasy do <xref:System.Windows.Media.RectangleGeometry>animowania właściwości . . Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:  
  
1. W ciągu pierwszych dwóch sekund używa <xref:System.Windows.Media.Animation.LinearRectKeyFrame> wystąpienia klasy do animowania stopniowej zmiany pozycji, szerokości i wysokości prostokąta. Liniowe klatki <xref:System.Windows.Media.Animation.LinearRectKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.  
  
2. Pod koniec następnej połowy sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> klasy, aby nagle zmniejszyć wysokość prostokąta. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> kluczowe, takie jak tworzenie nagłych zmian między wartościami, to znaczy, spadek wysokości występuje szybko i nie jest subtelny.  
  
3. W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineRectKeyFrame> wystąpienia klasy, aby zmienić prostokąt z powrotem do jego pierwotnego rozmiaru i położenia. Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineRectKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości. W tym przykładzie zmiana rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
