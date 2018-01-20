---
title: "Jak animować położenie obiektu z wykorzystaniem PointAnimation"
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
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f741770077a90bef33d75640726019496fe8eb8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Jak animować położenie obiektu z wykorzystaniem PointAnimation
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.PointAnimation> klasy do animowania obiektu wzdłuż <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przenosi elipsy <xref:System.Windows.Shapes.Path> z jednego miejsca na ekranie do innego. Przykład animuje pozycja <xref:System.Windows.Media.EllipseGeometry> za pomocą <xref:System.Windows.Media.Animation.PointAnimation> do animowania <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [Synchronizację](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
