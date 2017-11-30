---
title: "Jak określić czy przedział czasowy automatycznie odtwarza od końca"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2abce54905f0bb06bf983c065e064ce2dfeba932
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Jak określić czy przedział czasowy automatycznie odtwarza od końca
Oś czasu <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość określa, czy odtwarza odwrotnie po zakończeniu przekazywania iteracji. W poniższym przykładzie pokazano kilka animacji z identycznymi czas trwania i wartości docelowych, ale z różnymi <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ustawienia. Aby zademonstrować sposób <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości zachowuje się z różnymi <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , niektórych animacji ustawienia Powtórz. Ostatni pokazuje animacji jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości działa na zagnieżdżonych osi czasu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
