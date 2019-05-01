---
title: 'Instrukcje: Maluj obszar za pomocą rysowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010088"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="0faf2-102">Instrukcje: Maluj obszar za pomocą rysowania</span><span class="sxs-lookup"><span data-stu-id="0faf2-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="0faf2-103">Ten przykład pokazuje, jak malować obszar za pomocą rysowania.</span><span class="sxs-lookup"><span data-stu-id="0faf2-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="0faf2-104">Maluj obszar za pomocą rysowania, należy użyć <xref:System.Windows.Media.DrawingBrush> oraz jednego lub więcej <xref:System.Windows.Media.Drawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0faf2-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="0faf2-105">W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> namalować obiektu za pomocą rysowania dwie elipsy.</span><span class="sxs-lookup"><span data-stu-id="0faf2-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0faf2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0faf2-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="0faf2-107">Poniższa ilustracja przedstawia przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="0faf2-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="0faf2-108">![Dane wyjściowe z DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="0faf2-108">![Output from a DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="0faf2-109">(Środek kształt jest białe powodów opisanych w [Kontroluj wypełnienie kształtu złożonego](how-to-control-the-fill-of-a-composite-shape.md).)</span><span class="sxs-lookup"><span data-stu-id="0faf2-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="0faf2-110">Ustawiając <xref:System.Windows.Media.DrawingBrush> obiektu <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości, można utworzyć powtarzające się wzorca.</span><span class="sxs-lookup"><span data-stu-id="0faf2-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="0faf2-111">Poniższy przykład umożliwia malowanie obiektu z wzorcem utworzone na podstawie rysunku dwie elipsy.</span><span class="sxs-lookup"><span data-stu-id="0faf2-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="0faf2-112">Na poniższej ilustracji przedstawiono fragmentacji <xref:System.Windows.Media.DrawingBrush> danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="0faf2-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="0faf2-113">![Sąsiadująco w danych wyjściowych z DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="0faf2-113">![Tiled output from a DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="0faf2-114">Aby uzyskać więcej informacji na temat rysowania pędzle zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="0faf2-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="0faf2-115">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0faf2-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](drawing-objects-overview.md).</span></span>
