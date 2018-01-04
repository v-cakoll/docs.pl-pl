---
title: "Jak kontrolować animację z użyciem od, do i przez"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17f87c8bcf09022aa389df779e29f5e5affabc20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Jak kontrolować animację z użyciem od, do i przez
"Z lub do/przez" lub "animacji podstawowe" tworzy przejście między dwóch wartości docelowych (zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) wprowadzenie do różnych typów animacji). Aby ustawić wartości docelowe podstawowe animacji, użyj jej <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.  W poniższej tabeli przedstawiono sposób <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości, które mogą być używane razem lub oddzielnie określ docelowy animacji wartości.  
  
|Określono właściwości|Efekty|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Realizowany animacji z wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości do wartości podstawowej animowanej właściwości lub poprzedniej animacji wyjściowy wartość, w zależności od sposobu skonfigurowania poprzedniej animacji.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>i<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Realizowany animacji z wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>i<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Realizowany animacji z wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość określoną przez sumę <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animacja postępu od wartości podstawowej animowanej właściwości lub poprzedniej animacji wyjściowy wartość wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Realizowany animacji od wartości podstawowej animowanej właściwości lub poprzedniej animacji wyjściowy wartość sumę tę wartość i wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.|  
  
> [!NOTE]
>  Nie ustawiaj zarówno <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości w tym samym animacji.  
  
 Aby użyć innych metod interpolacji lub animować między więcej niż dwóch wartości docelowych, użyj klatek kluczowych animacji. Zobacz [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) Aby uzyskać więcej informacji.  
  
 Informacje o zastosowaniu wielu animacji do jednej właściwości, zobacz [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 W poniższym przykładzie pokazano różnych skutków ustawienie <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości animacji.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Z, aby i przykładowe wartości docelowej animacji](http://go.microsoft.com/fwlink/?LinkID=159988)
