---
title: Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141176"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności
W tym przykładzie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pokazano, jak <xref:System.Windows.Media.Animation.Timeline> określić dla nieaktywne animowane właściwości.  
  
## <a name="example"></a>Przykład  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a <xref:System.Windows.Media.Animation.Timeline> określa, co dzieje się z wartością animowanej właściwości, gdy <xref:System.Windows.Media.Animation.Timeline> nie jest animowany, <xref:System.Windows.Media.Animation.Timeline> to znaczy, gdy jest nieaktywny, ale jego element nadrzędny znajduje się wewnątrz jego aktywnego lub okresu wstrzymania. Na przykład animowana właściwość pozostaje na swojej wartości końcowej po zakończeniu animacji lub powraca do wartości, którą miała przed rozpoczęciem animacji?  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów. Każdy prostokąt używa innego <xref:System.Windows.Media.Animation.Timeline> obiektu.  
  
 Jeden <xref:System.Windows.Media.Animation.Timeline> ma, że jest ustawiona <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> na <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, <xref:System.Windows.Media.Animation.Timeline> aby powrócić do jego wartości nieanimowany po zakończeniu. Drugi <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>co powoduje, że szerokość pozostaje na <xref:System.Windows.Media.Animation.Timeline> jego wartości końcowej, gdy kończy.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykładowa galeria animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Przegląd Animacja](animation-overview.md)
- [Animacja i chronometraż Tematy porad](animation-and-timing-how-to-topics.md)
