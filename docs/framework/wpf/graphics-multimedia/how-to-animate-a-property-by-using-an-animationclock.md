---
title: "Jak animować właściwość przy użyciu AnimationClock"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145ff1be88f1af6692a8cf374e871479ed38d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Jak animować właściwość przy użyciu AnimationClock
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.Clock> obiekty do animowania właściwości.  
  
 Istnieją trzy sposoby do animowania właściwości zależności:  
  
-   Utwórz <xref:System.Windows.Media.Animation.AnimationTimeline> i powiązać ją z tej właściwości przy użyciu <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Użyj obiektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metodę, aby zastosować jedną <xref:System.Windows.Media.Animation.AnimationTimeline> do właściwości docelowej.  
  
-   Utwórz <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> i zastosować je do właściwości.  
  
 <xref:System.Windows.Media.Animation.Storyboard>obiekty i <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody umożliwiają animowania właściwości bez bezpośredniego tworzenia i dystrybuowania zegary (przykłady można znaleźć [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) i [animowania właściwości bez Przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); zegary są tworzone i automatycznie dystrybuowane automatycznie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do dwóch podobnych właściwości.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Na przykład przedstawiający sposób kontrolowania interaktywnie <xref:System.Windows.Media.Animation.Clock> po jej uruchomieniu, zobacz [interaktywnie sterować zegar](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animowanie właściwości bez użycia scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
