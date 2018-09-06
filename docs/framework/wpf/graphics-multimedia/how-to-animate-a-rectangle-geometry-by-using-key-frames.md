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
ms.openlocfilehash: 9b4a620ea58026c3be1b09d01a595e965e4c2b45
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43722934"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Jak animować geometrię prostokąta z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.RectangleGeometry.Rect%2A> właściwość <xref:System.Windows.Media.RectangleGeometry> przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.RectangleGeometry.Rect%2A> właściwość <xref:System.Windows.Media.RectangleGeometry>. Ta animacja używa trzech ramek kluczowych w następujący sposób:  
  
1.  Podczas pierwszych dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.LinearRectKeyFrame> klasy, aby animować stopniowego zmianę pozycję, szerokość i wysokość prostokąta. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearRectKeyFrame> utworzyć płynne przejście liniowy między wartościami.  
  
2.  Podczas koniec następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> klasy nagle zmniejszyć wysokość prostokąta. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> tworzenie nagłe zmiany między wartościami, to znaczy, zmniejszenie wysokości odbywa się szybko, a nie jest subtelne.  
  
3.  Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineRectKeyFrame> klasy, aby zmienić prostokąt, przywracając jego oryginalny rozmiar i położenie. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineRectKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> właściwości. W tym przykładzie zmiany rozpocznie się powoli i przyspiesza wykładniczo w kierunku końca odcinka czasu.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
