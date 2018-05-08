---
title: Jak ustawić czas trwania dla animacji
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: df9e12e1bd3a365c3013d0f75df663bd46186ee2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Jak ustawić czas trwania dla animacji
A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długość danego segmentu jest określany na osi czasu <xref:System.Windows.Duration>. Gdy <xref:System.Windows.Media.Animation.Timeline> rzędach jego trwania zatrzymuje odtwarzanie. Jeśli <xref:System.Windows.Media.Animation.Timeline> ma osi podrzędnej one zatrzymać odtwarzanie również. W przypadku animacji <xref:System.Windows.Duration> Określa, jak długo animacji umożliwia przejście ze swojej wartości początkowej, do jego wartości końcowej.  
  
 Można określić <xref:System.Windows.Duration> czasu określone, skończoną lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji musi być zawsze wartość czasu, ponieważ animacji zawsze musi mieć długość zdefiniowana, ograniczone — w przeciwnym razie animacji nie wiedział, jak przejście od jego wartości docelowych. Kontener osi czasu (<xref:System.Windows.Media.Animation.TimelineGroup> obiektów), takich jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, ma domyślny okres <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie.  
  
 W poniższych przykład szerokości, wysokości i wypełnienia kolor <xref:System.Windows.Shapes.Rectangle> jest animowany. Czas trwania są ustawiane na osiach czasu animacji i kontener skutki animacji, w tym kontrolowanie postrzegana prędkość animacji i zastępowanie czas trwania podrzędnych osi czasu z czasem trwania elementu timeline kontenera.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Duration>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
