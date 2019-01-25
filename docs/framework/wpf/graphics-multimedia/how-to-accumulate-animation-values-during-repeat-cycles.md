---
title: 'Instrukcje: Gromadź wartości animacji podczas cykli powtórzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 6e98b7eefd0c30e728b60926096c0f082bc079ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587284"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Instrukcje: Gromadź wartości animacji podczas cykli powtórzeń
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwość gromadzenie wartości animacji w cyklach.  
  
## <a name="example"></a>Przykład  
 Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości są gromadzone podstawowej wartości animacji w cyklach. Na przykład jeśli ustawisz powtarzanie 9 razy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") i ustaw właściwość animować od 10 do 15 (z = 10 = 15), animuje właściwość od 10 do 15 podczas pierwszego cyklu w 15-20 podczas drugiego cyklu , 20 – 25 podczas cyklu trzeci i tak dalej. Z tego powodu cyklu animacji używa końcową wartość animacji od poprzedniego cyklu animacji jako jego wartości bazowej.  
  
 Możesz użyć `IsCumulative` właściwość najbardziej podstawowym animacje i większości klatek kluczowych animacji. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [Przegląd Animacja kluczowych klatek](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Poniższy przykład przedstawia tego zachowania, animowanie szerokość cztery prostokąty. Przykład:  
  
-   Animuje pierwszy prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwość `true`.  
  
-   Animuje drugi prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości wartość domyślna `false`.  
  
-   Animuje trzeci prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwość `true`.  
  
-   Animuje ostatniego prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwość `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [Powtarzanie animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
