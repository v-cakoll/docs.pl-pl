---
title: Jak animować double z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344940"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Jak animować double z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Double> wartość właściwości, która przyjmuje za pomocą klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przesuwa prostokąt na ekranie. W <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> przykładzie użyto klasy <xref:System.Windows.Media.TranslateTransform.X%2A> do animowania właściwości zastosowanego <xref:System.Windows.Media.TranslateTransform> do . <xref:System.Windows.Shapes.Rectangle> Ta animacja, która powtarza się przez czas nieokreślony, używa trzech klatek kluczowych w następujący sposób:  
  
1. W ciągu pierwszych trzech sekund używa <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> wystąpienia klasy, aby przenieść prostokąt wzdłuż ścieżki ze stałą szybkością od pozycji początkowej do pozycji 500. Liniowe klatki <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.  
  
2. Na końcu czwartej sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> klasy, aby nagle przenieść prostokąt do następnej pozycji. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami. W tym przykładzie prostokąt znajduje się w pozycji początkowej, a następnie nagle pojawia się w pozycji 500.  
  
3. W ostatnich dwóch sekundach używa wystąpienia <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> klasy, aby przenieść prostokąt z powrotem do pozycji wyjściowej. Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartością właściwości. W tym przykładzie prostokąt rozpoczyna się od powolnego poruszania się, a następnie przyspiesza wykładniczo pod koniec segmentu czasu.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Aby uzyskać spójność z innymi przykładami animacji, wersje kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> używają obiektu do zastosowania pliku <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternatywnie podczas stosowania pojedynczej animacji w kodzie łatwiej <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jest użyć metody <xref:System.Windows.Media.Animation.Storyboard>zamiast używać . Na przykład zobacz [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
