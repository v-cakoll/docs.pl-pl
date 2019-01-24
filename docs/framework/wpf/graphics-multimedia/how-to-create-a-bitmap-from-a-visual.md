---
title: 'Instrukcje: Utwórz mapę bitową z Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: dbbf7691508e5e5ddf3ed3af768f757ee0c3f20c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705460"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Instrukcje: Utwórz mapę bitową z Visual
W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> jest renderowany przy użyciu <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Jest następnie renderowany na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> Tworzenie mapy bitowej danego tekstu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.DrawingContext>
- [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
- [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Użycie obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
