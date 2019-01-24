---
title: 'Instrukcje: Uprość animacje przy użyciu podrzędnych szeregów czasowych'
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: b5af20ce791c442eada0774cd46f52205e5b93e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648196"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Instrukcje: Uprość animacje przy użyciu podrzędnych szeregów czasowych
W tym przykładzie pokazano, jak uprościć animacje przy użyciu podrzędnych <xref:System.Windows.Media.Animation.ParallelTimeline> obiektów. A <xref:System.Windows.Media.Animation.Storyboard> jest typem <xref:System.Windows.Media.Animation.Timeline> zawierające informacje określania wartości docelowej dla osi czasu zawiera. Użyj <xref:System.Windows.Media.Animation.Storyboard> umożliwia określanie wartości docelowej informacji, w tym informacje o obiekcie i właściwości osi czasu.  
  
 Aby rozpocząć animacji, użyj jednego lub kilku <xref:System.Windows.Media.Animation.ParallelTimeline> obiektów jako elementy podrzędne zagnieżdżonych <xref:System.Windows.Media.Animation.Storyboard>. Te <xref:System.Windows.Media.Animation.ParallelTimeline> obiekty mogą zawierać inne animacji i dlatego lepiej umożliwiająca Hermetyzowanie sekwencje chronometrażu w złożonych animacji. Na przykład, jeśli użytkownik animuje <xref:System.Windows.Controls.TextBlock> i kilku kształtów w tej samej <xref:System.Windows.Media.Animation.Storyboard>, można oddzielić animacji dla <xref:System.Windows.Controls.TextBlock> i kształty, umieszczenie każdej w oddzielnych <xref:System.Windows.Media.Animation.ParallelTimeline>. Ponieważ każdy <xref:System.Windows.Media.Animation.ParallelTimeline> ma swój własny <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> i wszystkie elementy podrzędne elementu <xref:System.Windows.Media.Animation.ParallelTimeline> rozpocząć względem to <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, czas jest lepiej hermetyzowana.  
  
 Poniższy przykład animuje dwóch fragmentów tekstu (<xref:System.Windows.Controls.TextBlock> obiektów) ze w tej samej <xref:System.Windows.Media.Animation.Storyboard>. A <xref:System.Windows.Media.Animation.ParallelTimeline> hermetyzuje animacji w jednej z <xref:System.Windows.Controls.TextBlock> obiektów.  
  
 **Wydajność Pamiętaj:** Mimo że można zagnieżdżać <xref:System.Windows.Media.Animation.Storyboard> osi czasu wewnątrz siebie nawzajem <xref:System.Windows.Media.Animation.ParallelTimeline>s są bardziej odpowiednie na potrzeby zagnieżdżania, ponieważ wymagają one mniejsze obciążenie. ( <xref:System.Windows.Media.Animation.Storyboard> Klasa dziedziczy <xref:System.Windows.Media.Animation.ParallelTimeline> klasy.)  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Określanie elementu HandoffBehavior między animacjami scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
