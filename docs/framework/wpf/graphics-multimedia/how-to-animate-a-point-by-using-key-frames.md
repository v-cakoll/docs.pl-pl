---
title: 'Instrukcje: Animowanie punktu przy użyciu klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: b706568a0e8221aac737780592882f728f0f9e9c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328780"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Instrukcje: Animowanie punktu przy użyciu klatek kluczowych
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Point>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje przeniesienie elipsę trójkątna ścieżce. W przykładzie użyto <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwość <xref:System.Windows.Media.EllipseGeometry>. Ta animacja używa trzech ramek kluczowych w następujący sposób:  
  
1. Podczas pierwszego pół sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearPointKeyFrame> klasy, aby przenieść elipsy na ścieżce według stałej stawki z pozycji początkowej. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearPointKeyFrame> utworzyć płynne interpolacji liniowej między wartościami.  
  
2. Podczas koniec następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> klasy nagle przenieść elipsy wzdłuż ścieżki do następnego położenia. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> tworzenie nagłe skoki między wartościami.  
  
3. Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplinePointKeyFrame> klasy, aby przenieść elipsę z powrotem do jego pozycja początkowa. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplinePointKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> właściwości. W tym przykładzie animacji rozpocznie się powoli i przyspiesza wykładniczo w kierunku końca odcinka czasu.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Aby zachować spójność z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt, aby zastosować <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Jednak podczas stosowania pojedynczej animacji w kodzie, jest łatwiejszy w obsłudze <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
