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
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="d7a49-102">Instrukcje: Kodowanie wizualizacji do pliku obrazu</span><span class="sxs-lookup"><span data-stu-id="d7a49-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="d7a49-103">Ten przykład ilustruje sposób kodowania <xref:System.Windows.Media.Visual> obiektu do pliku obrazu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> przy użyciu i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="d7a49-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7a49-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7a49-104">Example</span></span>  
 <span data-ttu-id="d7a49-105">Jest tworzony <xref:System.Windows.Media.FormattedText> przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap>i, który jest renderowany do. <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.DrawingVisual></span><span class="sxs-lookup"><span data-stu-id="d7a49-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="d7a49-106">Renderowane mapy bitowe są następnie używane do utworzenia <xref:System.Windows.Media.Imaging.BitmapFrame> , która jest dodawana do programu <xref:System.Windows.Media.Imaging.PngBitmapEncoder> w celu utworzenia nowego pliku Portable Network Graphics (PNG).</span><span class="sxs-lookup"><span data-stu-id="d7a49-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new Portable Network Graphics (PNG) file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="d7a49-107">Użyto <xref:System.Windows.Media.Imaging.PngBitmapEncoder> w tym przykładzie, ale można było użyć dowolnego z <xref:System.Windows.Media.Imaging.BitmapEncoder> obiektów pochodnych do utworzenia pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="d7a49-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a49-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7a49-108">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="d7a49-109">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="d7a49-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="d7a49-110">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="d7a49-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="d7a49-111">Użycie obiektów DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="d7a49-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
