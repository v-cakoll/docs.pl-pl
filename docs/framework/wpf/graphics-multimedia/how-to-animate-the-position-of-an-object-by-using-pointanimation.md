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
ms.openlocfilehash: 6590c79ac6b6f104d9944a32da4c99318d334eec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafika i Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [Synchronizację](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
