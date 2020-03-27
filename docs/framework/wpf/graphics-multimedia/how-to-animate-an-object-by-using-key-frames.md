---
title: Jak animować obiekt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344705"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Jak animować obiekt z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Page.Background%2A> obiekt, <xref:System.Windows.Controls.Page> który w tym przykładzie jest właściwością formantu, przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> użyto klasy do <xref:System.Windows.Controls.Page.Background%2A> animowania <xref:System.Windows.Controls.Page> zmian kolorów właściwości formantu. Przykładowa animacja zmienia się na inny pędzel tła w regularnych odstępach czasu. Ta animacja <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> używa klasy do utworzenia trzech różnych klatek kluczowych. Animacja używa klatek kluczowych w następujący sposób:  
  
1. Na końcu pierwszej sekundy animuje wystąpienie <xref:System.Windows.Media.LinearGradientBrush> klasy. W tej sekcji przykładu stosuje się gradient liniowy do koloru tła, dzięki czemu kolor przechodzi z żółtego na pomarańczowy na czerwony.  
  
2. Na końcu następnej sekundy animuje wystąpienie <xref:System.Windows.Media.RadialGradientBrush> klasy. W tej sekcji przykładu stosuje gradient promieniowy do koloru tła, dzięki czemu kolor przechodzi z białego na niebieski na czarny.  
  
3. Na końcu trzeciej sekundy animuje wystąpienie <xref:System.Windows.Media.DrawingBrush> klasy. W tej sekcji przykładu stosuje się wzorzec szachownicy do tła.  
  
4. Animacja rozpoczyna się ponownie i powtarza się przez czas nieokreślony.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>jest jedynym typem klatki kluczowej, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> której można używać z klasą. Klatki kluczowe, takie jak <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> tworzenie nagłych zmian wartości, to znaczy, zmiany kolorów w tym przykładzie występują nagle.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
