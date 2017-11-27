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
ms.openlocfilehash: 7aabb01d35e02323785b6bae0764a8d8bc636e16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Jak utworzyć mapę bitową z Visual
W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> jest odwzorowywany z <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Następnie jest renderowany do <xref:System.Windows.Media.Imaging.RenderTargetBitmap> tworzenia mapy bitowej danego tekstu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.DrawingContext>  
 [Omówienie tworzenia obrazu](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Rysowanie obiekty — omówienie](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
