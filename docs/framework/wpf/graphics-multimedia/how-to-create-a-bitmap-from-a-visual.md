---
title: 'Instrukcje: Tworzenie mapy bitowej za pomocą wizualizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910263"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Instrukcje: Tworzenie mapy bitowej za pomocą wizualizacji
W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> jest renderowany przy użyciu <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Jest następnie renderowany na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> Tworzenie mapy bitowej danego tekstu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingContext>
- [Obrazowanie — przegląd](imaging-overview.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
