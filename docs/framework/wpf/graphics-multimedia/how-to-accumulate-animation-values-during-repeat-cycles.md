---
title: 'Instrukcje: Gromadzenie wartości animacji podczas cykli powtórzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 4b739883322751e2df86e13bfd07249abdb10a08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146019"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Instrukcje: Gromadzenie wartości animacji podczas cykli powtórzeń
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwość gromadzenie wartości animacji w cyklach.  
  
## <a name="example"></a>Przykład  
 Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości są gromadzone podstawowej wartości animacji w cyklach. Na przykład jeśli ustawisz powtarzanie 9 razy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") i ustaw właściwość animować od 10 do 15 (z = 10 = 15), animuje właściwość od 10 do 15 podczas pierwszego cyklu w 15-20 podczas drugiego cyklu , 20 – 25 podczas cyklu trzeci i tak dalej. Z tego powodu cyklu animacji używa końcową wartość animacji od poprzedniego cyklu animacji jako jego wartości bazowej.  
  
 Możesz użyć `IsCumulative` właściwość najbardziej podstawowym animacje i większości klatek kluczowych animacji. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](animation-overview.md) i [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).  
  
 Poniższy przykład przedstawia tego zachowania, animowanie szerokość cztery prostokąty. Przykład:  
  
-   Animuje pierwszy prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwość `true`.  
  
-   Animuje drugi prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości wartość domyślna `false`.  
  
-   Animuje trzeci prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwość `true`.  
  
-   Animuje ostatniego prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwość `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [Powtarzanie animacji](how-to-repeat-an-animation.md)
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [— Tematy porad](animation-and-timing-how-to-topics.md)
