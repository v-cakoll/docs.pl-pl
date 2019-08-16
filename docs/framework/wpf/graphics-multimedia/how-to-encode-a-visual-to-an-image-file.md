---
title: 'Instrukcje: Kodowanie wizualizacji do pliku obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545288"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Instrukcje: Kodowanie wizualizacji do pliku obrazu
Ten przykład ilustruje sposób kodowania <xref:System.Windows.Media.Visual> obiektu do pliku obrazu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> przy użyciu i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Przykład  
 Jest tworzony <xref:System.Windows.Media.FormattedText> przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap>i, który jest renderowany do. <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.DrawingVisual> Renderowane mapy bitowe są następnie używane do utworzenia <xref:System.Windows.Media.Imaging.BitmapFrame> , która jest dodawana do programu <xref:System.Windows.Media.Imaging.PngBitmapEncoder> w celu utworzenia nowego pliku Portable Network Graphics (PNG).  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 Użyto <xref:System.Windows.Media.Imaging.PngBitmapEncoder> w tym przykładzie, ale można było użyć dowolnego z <xref:System.Windows.Media.Imaging.BitmapEncoder> obiektów pochodnych do utworzenia pliku obrazu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingContext>
- [Obrazowanie — przegląd](imaging-overview.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
