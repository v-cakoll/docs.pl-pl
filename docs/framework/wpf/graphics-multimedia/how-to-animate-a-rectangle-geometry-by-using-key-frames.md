---
title: 'Instrukcje: Animowanie geometrii prostokąta przy użyciu klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311347"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Instrukcje: Animowanie geometrii prostokąta przy użyciu klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.RectangleGeometry.Rect%2A> właściwość <xref:System.Windows.Media.RectangleGeometry> przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.RectangleGeometry.Rect%2A> właściwość <xref:System.Windows.Media.RectangleGeometry>. Ta animacja używa trzech ramek kluczowych w następujący sposób:  
  
1. Podczas pierwszych dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.LinearRectKeyFrame> klasy, aby animować stopniowego zmianę pozycję, szerokość i wysokość prostokąta. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearRectKeyFrame> utworzyć płynne przejście liniowy między wartościami.  
  
2. Podczas koniec następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> klasy nagle zmniejszyć wysokość prostokąta. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> tworzenie nagłe zmiany między wartościami, to znaczy, zmniejszenie wysokości odbywa się szybko, a nie jest subtelne.  
  
3. Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineRectKeyFrame> klasy, aby zmienić prostokąt, przywracając jego oryginalny rozmiar i położenie. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineRectKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> właściwości. W tym przykładzie zmiany rozpocznie się powoli i przyspiesza wykładniczo w kierunku końca odcinka czasu.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
