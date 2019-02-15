---
title: 'Instrukcje: Powtórz animację'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 358400c07ec2e96401d95929cbdd22784db630f9
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305145"
---
# <a name="how-to-repeat-an-animation"></a>Instrukcje: Powtórz animację
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> w celu sterowania zachowaniem Powtórz animację.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, ile razy animacji powtarza proste czas jego trwania. Za pomocą <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, można określić, że <xref:System.Windows.Media.Animation.Timeline> powtarza określoną liczbę razy (liczba iteracji) lub w określonym przedziale czasu. W obu przypadkach animacji przechodzi przez dowolną liczbę przebiegów początku do końca, których potrzebuje, aby wypełnić żądana liczba lub czas trwania.  
  
 Domyślnie osie czasu mają liczbę powtórzeń 1.0, co oznacza odtwarzania jeden raz, a nie powtarzaj. Jednak jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, oś czasu jest powtarzany na czas nieokreślony.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości do sterowania zachowaniem powtarzanie animacji. Przykład animuje <xref:System.Windows.FrameworkElement.Width%2A> właściwość pięć prostokąty z każdego prostokąta przy użyciu innego typu zachowanie Powtórz tę procedurę.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Zobacz także
- [Gromadzenie wartości animacji podczas cykli powtórzeń](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Określanie, czy oś czasu ma być automatycznie odtwarzana od końca](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Animacja i chronometraż tematy porad](animation-and-timing-how-to-topics.md)
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970)
