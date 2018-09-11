---
title: Jak określić HandoffBehavior między animacjami scenorysu
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: 6846cde9fd0aa93a0ce57fd2da0f9e1df85ec5a4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264457"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Jak określić HandoffBehavior między animacjami scenorysu
W tym przykładzie pokazano, jak określić zachowanie dotyczące przekazania między animacjami scenorysu. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.BeginStoryboard> Określa, jak nowe animacji interakcji z wszelkie istniejące, które już są stosowane do właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa przyciski powiększania, gdy kursor myszy przesuwa się nad nimi, które stają się mniejsza, gdy kursor przesuwa się natychmiast. Jeśli wskaźnik myszy na przycisku i szybko usunąć kursor drugiej animacji będą stosowane przed zakończeniem pierwszy z nich. Jest to, gdy dwa animacji nakładają się następująco, które mogą zobaczyć różnicę między <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> wartości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> i <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Wartość <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> łączy nakładających się animacji, powodując gładkie przejście między animacjami podczas wartość <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> powoduje, że nowej animacji od razu zastąpić wcześniej nakładających się animacji.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacja i chronometraż](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
