---
title: Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452977"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="a6d5d-102">Jak narysować kształt zamknięty przy użyciu elementu wielobocznego</span><span class="sxs-lookup"><span data-stu-id="a6d5d-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="a6d5d-103">Ten przykład pokazuje, jak narysować zamknięty kształt przy użyciu elementu <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="a6d5d-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="a6d5d-104">Aby narysować zamknięty kształt, Utwórz element <xref:System.Windows.Shapes.Polygon> i użyj jego właściwości <xref:System.Windows.Shapes.Polygon.Points%2A>, aby określić wierzchołki kształtu.</span><span class="sxs-lookup"><span data-stu-id="a6d5d-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="a6d5d-105">Zostanie automatycznie narysowana linia łącząca pierwszy i ostatni punkt.</span><span class="sxs-lookup"><span data-stu-id="a6d5d-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="a6d5d-106">Na koniec Określ <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>lub oba te elementy.</span><span class="sxs-lookup"><span data-stu-id="a6d5d-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6d5d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6d5d-107">Example</span></span>  
 <span data-ttu-id="a6d5d-108">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]prawidłowa składnia dla punktów to rozdzielana spacjami lista par współrzędnych x i y oddzielanych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a6d5d-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="a6d5d-109">Chociaż w przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierać wielokąty, można użyć elementów wielokąt (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control>, który obsługuje zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="a6d5d-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="a6d5d-110">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="a6d5d-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>
