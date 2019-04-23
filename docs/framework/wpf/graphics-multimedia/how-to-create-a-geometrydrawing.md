---
title: 'Instrukcje: Tworzenie elementu GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: f5cdcfdb68ad8030bcbd6c689f45a8baddd000e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179793"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="88b43-102">Instrukcje: Tworzenie elementu GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="88b43-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="88b43-103">W tym przykładzie pokazano, jak utworzyć i wyświetlić <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="88b43-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="88b43-104">A <xref:System.Windows.Media.GeometryDrawing> pozwala na tworzenie kształt z wypełnieniem lecz konspektu, kojarząc <xref:System.Windows.Media.Pen> i <xref:System.Windows.Media.Brush> z <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="88b43-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="88b43-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Opisujący strukturę kształtu <xref:System.Windows.Media.GeometryDrawing.Brush%2A> opisuje wypełnienie kształtu i <xref:System.Windows.Media.GeometryDrawing.Pen%2A> opisuje kontur figury.</span><span class="sxs-lookup"><span data-stu-id="88b43-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b43-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="88b43-106">Example</span></span>  
 <span data-ttu-id="88b43-107">W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> do renderowania kształtu.</span><span class="sxs-lookup"><span data-stu-id="88b43-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="88b43-108">Kształt jest opisana przez <xref:System.Windows.Media.GeometryGroup> oraz dwóch <xref:System.Windows.Media.EllipseGeometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="88b43-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="88b43-109">Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej rysowania za pomocą <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="88b43-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="88b43-110"><xref:System.Windows.Media.GeometryDrawing> Jest wyświetlana przy użyciu <xref:System.Windows.Media.ImageDrawing> i <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="88b43-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="88b43-111">Na poniższej ilustracji przedstawiono wynikowe <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="88b43-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="88b43-112">![GeometryDrawing dwie elipsy](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="88b43-112">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="88b43-113">Do utworzenia bardziej złożonych rysunki, można połączyć wiele obiektów rysowania w jednym złożonego rysowania za pomocą <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="88b43-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b43-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88b43-114">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup>
- [<span data-ttu-id="88b43-115">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="88b43-115">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="88b43-116">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="88b43-116">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="88b43-117">Tworzenie złożonego rysunku</span><span class="sxs-lookup"><span data-stu-id="88b43-117">Create a Composite Drawing</span></span>](how-to-create-a-composite-drawing.md)
