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
ms.openlocfilehash: 872c19af0cfcf4fc980643c37e9a6028457c03b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096787"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Instrukcje: Kodowanie wizualizacji do pliku obrazu
W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Visual> obiektu do pliku obrazu przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.DrawingVisual> Jest tworzony przy użyciu <xref:System.Windows.Media.Imaging.BitmapImage> i <xref:System.Windows.Media.FormattedText> który jest renderowany do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>. Wyrenderowany mapy bitowej jest następnie używany do tworzenia <xref:System.Windows.Media.Imaging.BitmapFrame> który jest dodawany do <xref:System.Windows.Media.Imaging.PngBitmapEncoder> do tworzenia nowego [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] pliku.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> został użyty w tym przykładzie, ale żadnego z pochodnej <xref:System.Windows.Media.Imaging.BitmapEncoder> obiektów można użyć do utworzenia pliku obrazu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingContext>
- [Obrazowanie — przegląd](imaging-overview.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
