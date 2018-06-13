---
title: Jak gromadzić wartości animacji podczas cykli powtórzeń
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 7b954a388549f1bc6f3fa6ec1bcb2df61cc4e045
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557670"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Jak gromadzić wartości animacji podczas cykli powtórzeń
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> gromadzone przez powtarzające się cykle animacji wartości dla właściwości.  
  
## <a name="example"></a>Przykład  
 Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości gromadzone przez powtarzające się cykle wartości podstawowe animacji. Na przykład ustawić powtarzanie 9 razy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") i ustaw właściwość do animowania od 10 do 15 (z = 10 = 15), właściwość animuje od 10 do 15 podczas pierwszego cyklu od 15 do 20 podczas drugiego cyklu , 20 – 25 podczas cyklu trzeci i tak dalej. W związku z tym cyklu animacji używa wartości końcowej animacji od poprzedniego cyklu animacji jako jego wartość podstawową.  
  
 Można użyć `IsCumulative` właściwości z najprostszych animacji i większości klatek kluczowych animacji. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 W poniższym przykładzie pokazano to zachowanie przez szerokość cztery prostokąty animacji. Przykład:  
  
-   Animuje pierwszy prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości `true`.  
  
-   Animuje drugi prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości wartość domyślna wynosząca `false`.  
  
-   Animuje trzeci prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwości `true`.  
  
-   Animuje ostatniego prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwości `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [Powtarzanie animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
