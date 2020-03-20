---
title: Jak powtórzyć animację
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141552"
---
# <a name="how-to-repeat-an-animation"></a>Jak powtórzyć animację
W tym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pokazano, <xref:System.Windows.Media.Animation.Timeline> jak używać właściwości a w celu kontrolowania powtarzania zachowania animacji.  
  
## <a name="example"></a>Przykład  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> kontroluje, <xref:System.Windows.Media.Animation.Timeline> ile razy animacja powtarza jej prosty czas trwania. Za <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>pomocą programu można <xref:System.Windows.Media.Animation.Timeline> określić, że powtarza się przez określoną liczbę razy (liczba iteracji) lub przez określony okres czasu. W obu przypadkach animacji przechodzi przez tyle od początku do końca uruchamia, że potrzebuje, aby wypełnić żądaną liczbę lub czas trwania.  
  
 Domyślnie osie czasu mają liczbę powtórzeń 1.0, co oznacza, że grają jeden raz i nie powtarzają się. Jeśli jednak ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość a <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, oś czasu zostanie powtórzony przez czas nieokreślony.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pokazano, jak używać właściwości do kontrolowania powtarzania zachowania animacji. Przykład animuje <xref:System.Windows.FrameworkElement.Width%2A> właściwość pięciu prostokątów z każdego prostokąta przy użyciu innego typu zachowania powtarzania.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład zachowania chronometrażu animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).  
  
## <a name="see-also"></a>Zobacz też

- [Gromadzenie wartości animacji podczas cykli powtórzeń](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Określanie, czy oś czasu ma być automatycznie odtwarzana od końca](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Animacja i chronometraż Tematy porad](animation-and-timing-how-to-topics.md)
- [Przegląd Animacja](animation-overview.md)
- [Przykład zachowania chronometrażu animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
