---
title: "Jak obrócić element w miejscu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e7dac2b1afb9d0ed385f3c25c2e30a93ea8a24f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a>Jak obrócić element w miejscu
W tym przykładzie pokazano, jak utworzyć element pokrętła przy użyciu <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Następujący przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu. W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform>. Aby element pokrętła w miejscu, w przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości elementu w punkcie (0,5, 0,5).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Pełną przykładowej, który zawiera więcej przykładów przekształcania, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Przekształca — omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
