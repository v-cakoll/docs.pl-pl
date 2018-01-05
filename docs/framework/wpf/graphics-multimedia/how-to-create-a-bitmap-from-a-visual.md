---
title: "Jak utworzyć mapę bitową z Visual"
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
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db3ad547072f1d9162ede5c45144aa30e809c50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Jak utworzyć mapę bitową z Visual
W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> jest odwzorowywany z <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Następnie jest renderowany do <xref:System.Windows.Media.Imaging.RenderTargetBitmap> tworzenia mapy bitowej danego tekstu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.DrawingContext>  
 [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Użycie obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
