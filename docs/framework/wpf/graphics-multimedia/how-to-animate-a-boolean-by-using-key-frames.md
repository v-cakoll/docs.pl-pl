---
title: 'Instrukcje: Animuj boolean z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 503e8ec8bdaf88bcba4093075b1e7216b7cd3746
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361963"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a>Instrukcje: Animuj boolean z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować wartość właściwości typu Boolean <xref:System.Windows.Controls.Button> kontroli przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.UIElement.IsEnabled%2A> właściwość <xref:System.Windows.Controls.Button> kontroli. Klatek kluczowych w tym przykładzie są używane <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> klasy. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, jerky przepływu animacji.  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
