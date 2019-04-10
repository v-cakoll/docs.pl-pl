---
title: 'Instrukcje: Animowanie ciągu przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204175"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Instrukcje: Animowanie ciągu przy użyciu klatek kluczowych
W tym przykładzie pokazano, jak animować ciąg, który w tym przykładzie jest <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button> kontroli przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button>.  
  
 Klatek kluczowych w tym przykładzie są używane <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> klasy, ponieważ animacji ciąg, który jest tworzony z użyciem klatek kluczowych można używać tylko dyskretnych klatek kluczowych. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, zmiany w animacji wystąpić szybko i nie są subtelne.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
