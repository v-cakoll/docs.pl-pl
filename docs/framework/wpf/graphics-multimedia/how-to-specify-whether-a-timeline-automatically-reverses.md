---
title: 'Instrukcje: Określ czy przedział czasowy automatycznie odtwarza od końca'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354209"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Instrukcje: Określ czy przedział czasowy automatycznie odtwarza od końca
Oś czasu <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość określa, czy odtwarzany w odwrotnej kolejności po jej zakończeniu iteracji do przodu. W poniższym przykładzie pokazano kilka animacji przy użyciu identycznych czas trwania i wartości docelowych, ale z różnymi <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ustawienia. Aby zademonstrować sposób, w jaki <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość zachowuje się z różnymi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ustawienia, niektórych animacji są skonfigurowane do powtarzania. Ostatnie pokazuje animacji jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość pracuje zagnieżdżonych osi czasu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
