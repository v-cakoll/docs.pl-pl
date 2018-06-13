---
title: Jak powtórzyć animację
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: b2281805b62d6d4e639524d9a0959b392006d003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561212"
---
# <a name="how-to-repeat-an-animation"></a>Jak powtórzyć animację
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> w celu kontrolowania zachowania powtarzanie animacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, ile razy animacji powtarza jego długość proste. Za pomocą <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, można określić, że <xref:System.Windows.Media.Animation.Timeline> powtarza określoną liczbę razy (liczba iteracji) lub w określonym przedziale czasu. W obu przypadkach animacji przechodzi przez dowolną liczbę początku do końca uruchomień wymaganych w celu wypełnienia żądana liczba lub czas trwania.  
  
 Domyślnie osiach czasu mają liczbę powtórzeń 1.0, co oznacza odtworzony jeden raz i nie powtarzaj. Jednak jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, osi czasu jest powtarzany nieskończoność.  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości do sterowania zachowaniem powtarzanie animacji. Przykład animuje <xref:System.Windows.FrameworkElement.Width%2A> właściwości pięć prostokąty z każdego prostokąt przy użyciu innego typu zachowanie powtarzania.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Pełny przykład, zobacz [przykład zachowania chronometrażu animacji](http://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Zobacz też  
 [Gromadzenie wartości animacji podczas cykli powtórzeń](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Określanie, czy oś czasu ma być automatycznie odtwarzana od końca](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Synchronizację](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Przykład zachowania chronometrażu animacji](http://go.microsoft.com/fwlink/?LinkID=159970)
