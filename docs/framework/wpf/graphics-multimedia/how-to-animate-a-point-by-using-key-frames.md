---
title: Jak animować punkt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344881"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Jak animować punkt z wykorzystaniem klatek kluczowych
W tym przykładzie <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> pokazano, jak <xref:System.Windows.Point>używać klasy do animowania programu .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przenosi elipsę wzdłuż trójkątnej ścieżki. W przykładzie <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> użyto klasy <xref:System.Windows.Media.EllipseGeometry.Center%2A> do animowania właściwości . <xref:System.Windows.Media.EllipseGeometry>. Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:  
  
1. W pierwszej połowie drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.LinearPointKeyFrame> klasy, aby przenieść elipsy wzdłuż ścieżki w stałym tempie od pozycji wyjściowej. Liniowe klatki <xref:System.Windows.Media.Animation.LinearPointKeyFrame> kluczowe, takie jak tworzenie płynnej interpolacji liniowej między wartościami.  
  
2. Pod koniec następnej połowy sekundy, używa <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> wystąpienia klasy, aby nagle przenieść elipsy wzdłuż ścieżki do następnej pozycji. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami.  
  
3. W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplinePointKeyFrame> wystąpienia klasy, aby przenieść elipsę z powrotem do pozycji wyjściowej. Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplinePointKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości. W tym przykładzie animacja rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Aby uzyskać spójność z innymi przykładami animacji, wersje kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> używają obiektu do zastosowania pliku <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Jednak podczas stosowania pojedynczej animacji w kodzie łatwiej <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jest użyć metody <xref:System.Windows.Media.Animation.Storyboard>zamiast używać . Na przykład zobacz [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
