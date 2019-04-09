---
title: 'Instrukcje: Ustawianie czas trwania animacji'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198793"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Instrukcje: Ustawianie czas trwania animacji
A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długość danego segmentu jest ustalany na osi czasu <xref:System.Windows.Duration>. Gdy <xref:System.Windows.Media.Animation.Timeline> osiągnie koniec jego trwania przestaje odtwarzania. Jeśli <xref:System.Windows.Media.Animation.Timeline> podrzędnych osi czasu, ma także odtwarzanie one zatrzymane. W przypadku animacji <xref:System.Windows.Duration> określa animacji czas przejścia z jej wartość początkową wartość końcową.  
  
 Można określić <xref:System.Windows.Duration> przy użyciu określonych, skończony czas lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji musi być zawsze wartość czasu, ponieważ animacji zawsze musi mieć zdefiniowany, skończonego długość — w przeciwnym razie animacja będzie wiadomo, jak przejście pomiędzy jego wartości docelowej. Osie czasu kontenera (<xref:System.Windows.Media.Animation.TimelineGroup> obiektów), takie jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, mają domyślny czas trwania <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie.  
  
 W poniższy przykład szerokości, wysokości i wypełnienia kolor <xref:System.Windows.Shapes.Rectangle> jest animowany. Czas trwania są ustawione na osi czasu animacji i kontener skutkuje efektów animacji, w tym kontrolowanie postrzegany szybkość animacji i zastępowanie czas trwania podrzędnych osi czasu z czasem trwania osi czasu w kontenerze.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Duration>
- [Przegląd Animacja](animation-overview.md)
