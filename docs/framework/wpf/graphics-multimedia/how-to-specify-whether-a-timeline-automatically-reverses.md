---
title: Jak określić czy przedział czasowy automatycznie odtwarza od końca
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560068"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Jak określić czy przedział czasowy automatycznie odtwarza od końca
Oś czasu <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość określa, czy odtwarza odwrotnie po zakończeniu przekazywania iteracji. W poniższym przykładzie pokazano kilka animacji z identycznymi czas trwania i wartości docelowych, ale z różnymi <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ustawienia. Aby zademonstrować sposób <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości zachowuje się z różnymi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , niektórych animacji ustawienia Powtórz. Ostatni pokazuje animacji jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości działa na zagnieżdżonych osi czasu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
