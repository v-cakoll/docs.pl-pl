---
title: 'Instrukcje: Koduj Visual do pliku obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 2d5da0bde243128bc0d7aa29bf865ca9bfbd1d9a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356000"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="6ecf1-102">Instrukcje: Koduj Visual do pliku obrazu</span><span class="sxs-lookup"><span data-stu-id="6ecf1-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="6ecf1-103">W tym przykładzie pokazano, jak kodować <xref:System.Windows.Media.Visual> obiektu do pliku obrazu przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="6ecf1-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ecf1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ecf1-104">Example</span></span>  
 <span data-ttu-id="6ecf1-105"><xref:System.Windows.Media.DrawingVisual> Jest tworzony przy użyciu <xref:System.Windows.Media.Imaging.BitmapImage> i <xref:System.Windows.Media.FormattedText> który jest renderowany do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span><span class="sxs-lookup"><span data-stu-id="6ecf1-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="6ecf1-106">Wyrenderowany mapy bitowej jest następnie używany do tworzenia <xref:System.Windows.Media.Imaging.BitmapFrame> który jest dodawany do <xref:System.Windows.Media.Imaging.PngBitmapEncoder> do tworzenia nowego [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="6ecf1-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="6ecf1-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> został użyty w tym przykładzie, ale żadnego z pochodnej <xref:System.Windows.Media.Imaging.BitmapEncoder> obiektów można użyć do utworzenia pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="6ecf1-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ecf1-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ecf1-108">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="6ecf1-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="6ecf1-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="6ecf1-110">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="6ecf1-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="6ecf1-111">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="6ecf1-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
