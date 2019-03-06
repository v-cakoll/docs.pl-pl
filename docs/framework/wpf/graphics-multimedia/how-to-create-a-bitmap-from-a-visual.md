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
ms.openlocfilehash: 429aacc99d8ead5a18e9be7602b19a74773b419a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362867"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Instrukcje: Utwórz mapę bitową z Visual
W tym przykładzie pokazano, jak utworzyć mapę bitową z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> jest renderowany przy użyciu <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Jest następnie renderowany na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> Tworzenie mapy bitowej danego tekstu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.DrawingContext>
- [Obrazowanie — przegląd](imaging-overview.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
