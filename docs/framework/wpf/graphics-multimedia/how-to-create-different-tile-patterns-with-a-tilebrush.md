---
title: Jak utworzyć różne wzory sąsiadujących kafelek z użyciem TileBrush
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: 01004c66a8bd820f05e6e1f6c77a9fe7d30bca46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559604"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="9f2eb-102">Jak utworzyć różne wzory sąsiadujących kafelek z użyciem TileBrush</span><span class="sxs-lookup"><span data-stu-id="9f2eb-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="9f2eb-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.TileBrush> utworzyć wzorca.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="9f2eb-104"><xref:System.Windows.Media.TileBrush.TileMode%2A> Właściwości można określić sposób zawartości <xref:System.Windows.Media.TileBrush> jest powtarzany, oznacza to, sąsiadująco w celu wypełnienia obszaru wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="9f2eb-105">Aby utworzyć wzorzec, należy ustawić <xref:System.Windows.Media.TileBrush.TileMode%2A> do <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, lub <xref:System.Windows.Media.TileMode.FlipXY>.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="9f2eb-106">Należy także ustawić <xref:System.Windows.Media.TileBrush.Viewport%2A> z <xref:System.Windows.Media.TileBrush> , aby była mniejsza niż obszar malowanego; w przeciwnym razie pojedynczy fragment jest wyprodukowania, niezależnie od tego, co <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawienie używasz.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f2eb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f2eb-107">Example</span></span>  
 <span data-ttu-id="9f2eb-108">Poniższy przykład tworzy pięciu <xref:System.Windows.Media.DrawingBrush> obiektów, daje im każdej innej <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawienie i używa ich do malowania prostokąty pięć.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="9f2eb-109">Mimo że w tym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> klasy, aby zademonstrować <xref:System.Windows.Media.TileBrush.TileMode%2A> zachowanie, <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości działa tak samo dla wszystkich <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, że dla <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, i <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="9f2eb-110">Na poniższej ilustracji przedstawiono dane wyjściowe, który spowoduje utworzenie w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9f2eb-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="9f2eb-111">![Ustawianie widoku kafelków przykładowe dane wyjściowe TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="9f2eb-111">![TileBrush tiling example output](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="9f2eb-112">Wzorce kafelka utworzyć z właściwością TileMode</span><span class="sxs-lookup"><span data-stu-id="9f2eb-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="9f2eb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f2eb-113">See Also</span></span>  
 [<span data-ttu-id="9f2eb-114">Ustawianie rozmiaru kafelka dla elementu TileBrush</span><span class="sxs-lookup"><span data-stu-id="9f2eb-114">Set the Tile Size for a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [<span data-ttu-id="9f2eb-115">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="9f2eb-115">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
