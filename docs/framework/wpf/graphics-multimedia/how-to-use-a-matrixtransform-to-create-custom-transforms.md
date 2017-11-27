---
title: "Jak użyć MatrixTransform do utworzenia niestandardowych przekształceń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4995c5d712807e91b27c7afacd6f5b7015cb5898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Jak użyć MatrixTransform do utworzenia niestandardowych przekształceń
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.MatrixTransform> do tłumaczenia (przenoszenia) pozycji, rozciąganie i pochylanie z <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Użyj <xref:System.Windows.Media.MatrixTransform> klasy w celu utworzenia niestandardowych przekształceń, które nie są dostarczane przez <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, lub <xref:System.Windows.Media.TranslateTransform> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [Przekształca — omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Kształty i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
