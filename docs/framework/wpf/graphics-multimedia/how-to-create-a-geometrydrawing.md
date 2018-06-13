---
title: 'Porady: tworzenie GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 713cecd10bfa62494c50c96cb8cbece69f7e5660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560663"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="128f8-102">Porady: tworzenie GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="128f8-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="128f8-103">W tym przykładzie pokazano, jak utworzyć i wyświetlić <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="128f8-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="128f8-104">A <xref:System.Windows.Media.GeometryDrawing> umożliwia utworzenie kształt z wypełnieniem lecz konspektu przez skojarzenie <xref:System.Windows.Media.Pen> i <xref:System.Windows.Media.Brush> z <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="128f8-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="128f8-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Opisuje strukturę kształtu <xref:System.Windows.Media.GeometryDrawing.Brush%2A> opisuje wypełnienia kształtu i <xref:System.Windows.Media.GeometryDrawing.Pen%2A> opisuje konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="128f8-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="128f8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="128f8-106">Example</span></span>  
 <span data-ttu-id="128f8-107">W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> do renderowania kształtu.</span><span class="sxs-lookup"><span data-stu-id="128f8-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="128f8-108">Kształt jest opisane przez <xref:System.Windows.Media.GeometryGroup> i dwa <xref:System.Windows.Media.EllipseGeometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="128f8-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="128f8-109">Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej jest rysowany z <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="128f8-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="128f8-110"><xref:System.Windows.Media.GeometryDrawing> Jest wyświetlany za pomocą <xref:System.Windows.Media.ImageDrawing> i <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="128f8-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="128f8-111">Na poniższej ilustracji przedstawiono powstałe w ten sposób <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="128f8-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="128f8-112">![GeometryDrawing zawierający dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="128f8-112">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="128f8-113">Do tworzenia bardziej złożonych rysunków, można połączyć wiele obiektów rysowania w jednej złożonym Rysowanie za pomocą <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="128f8-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128f8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="128f8-114">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 [<span data-ttu-id="128f8-115">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="128f8-115">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="128f8-116">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="128f8-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="128f8-117">Tworzenie złożonego rysunku</span><span class="sxs-lookup"><span data-stu-id="128f8-117">Create a Composite Drawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
