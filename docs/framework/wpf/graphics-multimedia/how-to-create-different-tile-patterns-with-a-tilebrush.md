---
title: 'Instrukcje: Tworzenie różnych wzorów kafelkowych z użyciem elementu TileBrush'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: c1051b234961eee9ae740af2abac3d64c523656c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227408"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="4e90b-102">Instrukcje: Tworzenie różnych wzorów kafelkowych z użyciem elementu TileBrush</span><span class="sxs-lookup"><span data-stu-id="4e90b-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="4e90b-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.TileBrush> utworzyć wzorca.</span><span class="sxs-lookup"><span data-stu-id="4e90b-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="4e90b-104"><xref:System.Windows.Media.TileBrush.TileMode%2A> Właściwości można określić sposób, w jaki zawartości <xref:System.Windows.Media.TileBrush> jest powtarzany, to znaczy, sąsiadująco w celu wypełnienia obszaru danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4e90b-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="4e90b-105">Aby utworzyć wzorzec, należy ustawić <xref:System.Windows.Media.TileBrush.TileMode%2A> do <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, lub <xref:System.Windows.Media.TileMode.FlipXY>.</span><span class="sxs-lookup"><span data-stu-id="4e90b-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="4e90b-106">Należy także ustawić <xref:System.Windows.Media.TileBrush.Viewport%2A> z <xref:System.Windows.Media.TileBrush> tak, aby jego rozmiar jest mniejszy niż obszar malowanego; w przeciwnym razie pojedynczego kafelka jest utworzone, niezależnie od tego, co <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawienie używasz.</span><span class="sxs-lookup"><span data-stu-id="4e90b-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e90b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e90b-107">Example</span></span>  
 <span data-ttu-id="4e90b-108">Poniższy przykład tworzy pięć <xref:System.Windows.Media.DrawingBrush> obiektów, daje im każdego innego <xref:System.Windows.Media.TileBrush.TileMode%2A> ustawienie i używa ich do malowania pięć prostokąty.</span><span class="sxs-lookup"><span data-stu-id="4e90b-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="4e90b-109">Mimo że w tym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> klasę wykazać <xref:System.Windows.Media.TileBrush.TileMode%2A> zachowanie, <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości działa tak samo dla wszystkich <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, że dla <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, i <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="4e90b-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="4e90b-110">Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="4e90b-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="4e90b-111">![TileBrush fragmentacji przykładowe dane wyjściowe](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="4e90b-111">![TileBrush tiling example output](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="4e90b-112">Utworzone za pomocą właściwości TileMode wzorce kafelkowe</span><span class="sxs-lookup"><span data-stu-id="4e90b-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4e90b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e90b-113">See also</span></span>

- [<span data-ttu-id="4e90b-114">Ustawianie rozmiaru kafelka dla elementu TileBrush</span><span class="sxs-lookup"><span data-stu-id="4e90b-114">Set the Tile Size for a TileBrush</span></span>](how-to-set-the-tile-size-for-a-tilebrush.md)
- [<span data-ttu-id="4e90b-115">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="4e90b-115">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
