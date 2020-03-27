---
title: Jak animować ciąg z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344667"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Jak animować ciąg z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.ContentControl.Content%2A> ciąg, <xref:System.Windows.Controls.Button> który w tym przykładzie jest właściwością formantu przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> użyto <xref:System.Windows.Controls.ContentControl.Content%2A> klasy do <xref:System.Windows.Controls.Button>animowania właściwości . .  
  
 Wszystkie klatki kluczowe w tym przykładzie <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> używają wystąpienia klasy, ponieważ animacja ciągu utworzona za pomocą klatek kluczowych może używać tylko dyskretnych klatek kluczowych. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami, czyli zmiany animacji występują szybko i nie są subtelne.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
