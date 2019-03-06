---
title: 'Instrukcje: Określ FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1d6a3ec38a6488d997ce5a4734cc095446354070
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358135"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Instrukcje: Określ FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności
W tym przykładzie pokazano, jak określić <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dla nieaktywnych <xref:System.Windows.Media.Animation.Timeline> właściwości animowany.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, co się dzieje z wartości właściwości animowany, gdy nie jest animowany, oznacza to, kiedy <xref:System.Windows.Media.Animation.Timeline> jest nieaktywna, ale jego element nadrzędny <xref:System.Windows.Media.Animation.Timeline> znajduje się wewnątrz jego aktywny lub okres przechowywania. Na przykład, jest animowany właściwości pozostają w jego końcem wartości po animacji kończy się lub zrobi to przywrócić wartość miała zanim animacja została uruchomiona?  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów. Każdego prostokąta używa innego <xref:System.Windows.Media.Animation.Timeline> obiektu.  
  
 Jeden <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> który jest skonfigurowany do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, aby powrócić do jego bez — animowane wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy. Druga <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, co powoduje, że szerokość pozostaje na jej końcu wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Animacja — przegląd](animation-overview.md)
- [Animacja i chronometraż tematy porad](animation-and-timing-how-to-topics.md)
