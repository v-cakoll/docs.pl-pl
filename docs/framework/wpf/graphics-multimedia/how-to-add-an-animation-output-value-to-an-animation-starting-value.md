---
title: "Jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 018311acb1cfcdaf64dae7a6ea500f0fcca387fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji
W tym przykładzie przedstawiono sposób dodawania wartość wyjściowa animacji na wartość początkową animacji.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Właściwość określa, czy wartość wyjściowa dodane do początkowej wartości (podstawa) animowanej właściwości animacji. Można użyć <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> właściwości z najprostszych animacji i większości klatek kluczowych animacji. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 W poniższym przykładzie przedstawiono efekt użycia <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> właściwości o <xref:System.Windows.Media.Animation.DoubleAnimation> i przy użyciu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> właściwości o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Accumulate wartości animacji podczas cykli powtórzeń](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Omówienie klucza poklatkowych](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Synchronizację](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
