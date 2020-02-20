---
title: Jak utworzyć kształt złożony
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452100"
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="7d839-102">Jak utworzyć kształt złożony</span><span class="sxs-lookup"><span data-stu-id="7d839-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="7d839-103">Ten przykład pokazuje, jak tworzyć kształty złożone przy użyciu obiektów <xref:System.Windows.Media.Geometry> i wyświetlać je za pomocą elementu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="7d839-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="7d839-104">W poniższym przykładzie <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>i <xref:System.Windows.Media.RectangleGeometry> są używane z <xref:System.Windows.Media.GeometryGroup> do tworzenia kształtu złożonego.</span><span class="sxs-lookup"><span data-stu-id="7d839-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="7d839-105">Geometrie są następnie rysowane przy użyciu elementu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="7d839-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d839-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d839-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="7d839-107">Na poniższej ilustracji przedstawiono kształt utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d839-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="7d839-108">![Złożona Geometria utworzona przy użyciu elementu geometrycznego](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="7d839-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="7d839-109">Złożona Geometria</span><span class="sxs-lookup"><span data-stu-id="7d839-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="7d839-110">Bardziej złożone kształty, takie jak wielokąty i kształty z zakrzywionymi segmentami, można utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="7d839-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="7d839-111">Przykład przedstawiający sposób tworzenia kształtu przy użyciu <xref:System.Windows.Media.PathGeometry>można znaleźć w temacie [Tworzenie kształtu przy użyciu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="7d839-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="7d839-112">Chociaż ten przykład renderuje kształt na ekranie przy użyciu elementu <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Media.Geometry> obiekty mogą być również używane do opisywania zawartości <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="7d839-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="7d839-113">Mogą być również używane do przycinania i testowania trafień.</span><span class="sxs-lookup"><span data-stu-id="7d839-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="7d839-114">Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="7d839-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>
