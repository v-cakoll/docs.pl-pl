---
title: 'Instrukcje: Określanie elementu HandoffBehavior między animacjami scenorysu'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651041"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Instrukcje: Określanie elementu HandoffBehavior między animacjami scenorysu
W tym przykładzie pokazano, jak określić zachowanie dotyczące przekazania między animacjami scenorysu. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.BeginStoryboard> Określa, jak nowe animacji interakcji z wszelkie istniejące, które już są stosowane do właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa przyciski powiększania, gdy kursor myszy przesuwa się nad nimi, które stają się mniejsza, gdy kursor przesuwa się natychmiast. Jeśli wskaźnik myszy na przycisku i szybko usunąć kursor drugiej animacji będą stosowane przed zakończeniem pierwszy z nich. Jest to, gdy dwa animacji nakładają się następująco, które mogą zobaczyć różnicę między <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> wartości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> i <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Wartość <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> łączy nakładających się animacji, powodując gładkie przejście między animacjami podczas wartość <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> powoduje, że nowej animacji od razu zastąpić wcześniej nakładających się animacji.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [Animacja — przegląd](animation-overview.md)
- [Animacja i chronometraż tematy porad](animation-and-timing-how-to-topics.md)
