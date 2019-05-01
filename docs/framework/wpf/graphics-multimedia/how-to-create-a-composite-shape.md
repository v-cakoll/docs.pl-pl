---
title: 'Instrukcje: Tworzenie kształtu złożonego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: de9f7972c7a51ea623c3630fe62bb48f6109317e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052901"
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="cd6c2-102">Instrukcje: Tworzenie kształtu złożonego</span><span class="sxs-lookup"><span data-stu-id="cd6c2-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="cd6c2-103">W tym przykładzie przedstawiono sposób tworzenia złożonych kształtów za pomocą <xref:System.Windows.Media.Geometry> obiektów i wyświetlać je za pomocą <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="cd6c2-104">W poniższym przykładzie <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.RectangleGeometry> są używane wraz z <xref:System.Windows.Media.GeometryGroup> utworzyć kształt złożony.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="cd6c2-105">Geometrie są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd6c2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd6c2-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="cd6c2-107">Poniższa ilustracja przedstawia kształtem utworzona w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="cd6c2-108">![Złożone typy geometryczne, utworzony za pomocą GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="cd6c2-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="cd6c2-109">Złożone typy geometryczne</span><span class="sxs-lookup"><span data-stu-id="cd6c2-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="cd6c2-110">Bardziej złożonych kształtów, na przykład wielokątów i kształtów za pomocą punkty kontrolne mogą zostać utworzone za pomocą <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="cd6c2-111">Aby uzyskać przykład pokazujący, jak utworzyć kształt używając <xref:System.Windows.Media.PathGeometry>, zobacz [Utwórz kształt używając PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="cd6c2-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="cd6c2-112">Mimo że w tym przykładzie powoduje wyświetlenie kształt na ekranie za pomocą <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> obiektów może również służyć do opisu zawartość <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="cd6c2-113">Mogą one również służyć do przycinania i testowania trafień.</span><span class="sxs-lookup"><span data-stu-id="cd6c2-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="cd6c2-114">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="cd6c2-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
