---
title: Jak określić HandoffBehavior między animacjami scenorysu
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: c4728dc1cb4eeeff55e533b8d91e4512d9cc1d94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560554"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Jak określić HandoffBehavior między animacjami scenorysu
Ten przykład przedstawia sposób określania zachowania przekazaniem między animacje scenorysu. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.BeginStoryboard> określa sposób animacje interakcji z istniejących komunikatów, które już są stosowane do właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa przyciski powiększania, gdy wskaźnik myszy przesuwa się nad nimi, które stają się mniejszy, gdy kursor przesuwa optymalizacji. Jeśli wskaźnik myszy na przycisk, a następnie szybko Usuń kursora, drugi animacji zostaną zastosowane przed zakończeniem pierwszego z nich. Jest w przypadku dwóch animacje nakłada się na podobny do tego, które widać różnicę między <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> wartości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> i <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Wartość <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> łączy nakładające się animacji, powodując płynniejszy przejścia między animacji podczas wartość <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> powoduje, że nowe animacji natychmiast zastąpienie wcześniej nakładające się animacji.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Synchronizację](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
