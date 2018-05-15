---
title: Jak definiować prostokąt przy użyciu RectangleGeometry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 5d2ec6aec1eea8528ea6b43f72f4820b8bc19a37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="d8c81-102">Jak definiować prostokąt przy użyciu RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="d8c81-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="d8c81-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Media.RectangleGeometry> klasy do opisywania prostokąta.</span><span class="sxs-lookup"><span data-stu-id="d8c81-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8c81-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8c81-104">Example</span></span>  
 <span data-ttu-id="d8c81-105">Poniższy przykład przedstawia sposób tworzenia i renderowania <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="d8c81-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="d8c81-106">Względne położenie i wymiary prostokąta są definiowane przez <xref:System.Windows.Rect> struktury.</span><span class="sxs-lookup"><span data-stu-id="d8c81-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="d8c81-107">Względne położenie jest `50,50` i wysokość i szerokość są `25` tworzenie kwadrat.</span><span class="sxs-lookup"><span data-stu-id="d8c81-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="d8c81-108">Prostokąt wewnętrznego jest malowany <xref:System.Windows.Media.Brushes.LemonChiffon%2A> pędzla i konturu jej jest malowany <xref:System.Windows.Media.Brushes.Black%2A> grubość pociągnięć `1`.</span><span class="sxs-lookup"><span data-stu-id="d8c81-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="d8c81-109">![Obiekt RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="d8c81-109">![A RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="d8c81-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="d8c81-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="d8c81-111">Mimo że w tym przykładzie użyto <xref:System.Windows.Shapes.Path> element do renderowania <xref:System.Windows.Media.RectangleGeometry>, istnieje wiele sposobów używania <xref:System.Windows.Media.RectangleGeometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d8c81-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="d8c81-112">Na przykład <xref:System.Windows.Media.RectangleGeometry> może służyć do określenia <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> lub <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="d8c81-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="d8c81-113">Inne klasy proste geometrii obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="d8c81-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="d8c81-114">Te mają geometrię, a także bardziej złożonych z nich, można również tworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="d8c81-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c81-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8c81-115">See Also</span></span>  
 [<span data-ttu-id="d8c81-116">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="d8c81-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="d8c81-117">Tworzenie kształtu złożonego</span><span class="sxs-lookup"><span data-stu-id="d8c81-117">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="d8c81-118">Tworzenie kształtu przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="d8c81-118">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
