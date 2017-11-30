---
title: "Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b6617bdaa14f405e54af1709f0cf985911c56ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności
W tym przykładzie przedstawiono sposób określania <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dla nieaktywnych <xref:System.Windows.Media.Animation.Timeline> animowanej właściwości.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, co się dzieje z wartości właściwości animowany, gdy nie jest on animowany, oznacza to, kiedy <xref:System.Windows.Media.Animation.Timeline> jest nieaktywna, ale jego element nadrzędny <xref:System.Windows.Media.Animation.Timeline> znajduje się wewnątrz jego aktywny lub okres przechowywania. Na przykład jest właściwością animowany pozostają na jej końcu wartość po animacji kończy się lub nie go przywrócić wartość sprzed animacja została uruchomiona?  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów. Każdy prostokąt używa innej <xref:System.Windows.Media.Animation.Timeline> obiektu.  
  
 Jeden <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> który ustawiono <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, aby powrócić do jego z systemem innym niż — animowane wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy się. Druga <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, co powoduje, że szerokość pozostaje na jej końcu wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy się.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Pełny przykład, zobacz [galerii przykład animacji](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Synchronizację](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
