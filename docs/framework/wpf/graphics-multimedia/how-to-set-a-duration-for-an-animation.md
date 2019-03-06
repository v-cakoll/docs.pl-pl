---
title: 'Instrukcje: Ustaw czas trwania dla animacji'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: 83f87e911d9d5412eaba1eb88aea74b9325bc899
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351633"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Instrukcje: Ustaw czas trwania dla animacji
A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długość danego segmentu jest ustalany na osi czasu <xref:System.Windows.Duration>. Gdy <xref:System.Windows.Media.Animation.Timeline> osiągnie koniec jego trwania przestaje odtwarzania. Jeśli <xref:System.Windows.Media.Animation.Timeline> podrzędnych osi czasu, ma także odtwarzanie one zatrzymane. W przypadku animacji <xref:System.Windows.Duration> określa animacji czas przejścia z jej wartość początkową wartość końcową.  
  
 Można określić <xref:System.Windows.Duration> przy użyciu określonych, skończony czas lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji musi być zawsze wartość czasu, ponieważ animacji zawsze musi mieć zdefiniowany, skończonego długość — w przeciwnym razie animacja będzie wiadomo, jak przejście pomiędzy jego wartości docelowej. Osie czasu kontenera (<xref:System.Windows.Media.Animation.TimelineGroup> obiektów), takie jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, mają domyślny czas trwania <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie.  
  
 W poniższy przykład szerokości, wysokości i wypełnienia kolor <xref:System.Windows.Shapes.Rectangle> jest animowany. Czas trwania są ustawione na osi czasu animacji i kontener skutkuje efektów animacji, w tym kontrolowanie postrzegany szybkość animacji i zastępowanie czas trwania podrzędnych osi czasu z czasem trwania osi czasu w kontenerze.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Duration>
- [Animacja — przegląd](animation-overview.md)
