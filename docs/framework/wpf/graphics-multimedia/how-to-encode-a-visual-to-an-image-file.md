---
title: "Jak kodować Visual do pliku obrazu"
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
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88a5d93c9c4726d1f6493df28d0a2a559394ef74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Jak kodować Visual do pliku obrazu
W tym przykładzie pokazano sposób kodowania <xref:System.Windows.Media.Visual> obiektu do pliku obrazu przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.DrawingVisual> Jest tworzony przy użyciu <xref:System.Windows.Media.Imaging.BitmapImage> i <xref:System.Windows.Media.FormattedText> który jest renderowany do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>. Renderowany mapy bitowej jest następnie używany do tworzenia <xref:System.Windows.Media.Imaging.BitmapFrame> która jest dodawana do <xref:System.Windows.Media.Imaging.PngBitmapEncoder> do tworzenia nowego [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] pliku.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> został użyty w tym przykładzie, ale żadnego z pochodnej <xref:System.Windows.Media.Imaging.BitmapEncoder> obiektów można używać do utworzenia pliku obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.DrawingContext>  
 [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Użycie obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
