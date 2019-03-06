---
title: 'Instrukcje: Tworzenie GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 6eb604a8446000ef308c2b5a99480fb6a476c949
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373819"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="cb15f-102">Instrukcje: Tworzenie GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="cb15f-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="cb15f-103">W tym przykładzie pokazano, jak utworzyć i wyświetlić <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="cb15f-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="cb15f-104">A <xref:System.Windows.Media.GeometryDrawing> pozwala na tworzenie kształt z wypełnieniem lecz konspektu, kojarząc <xref:System.Windows.Media.Pen> i <xref:System.Windows.Media.Brush> z <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="cb15f-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="cb15f-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Opisujący strukturę kształtu <xref:System.Windows.Media.GeometryDrawing.Brush%2A> opisuje wypełnienie kształtu i <xref:System.Windows.Media.GeometryDrawing.Pen%2A> opisuje kontur figury.</span><span class="sxs-lookup"><span data-stu-id="cb15f-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb15f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb15f-106">Example</span></span>  
 <span data-ttu-id="cb15f-107">W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> do renderowania kształtu.</span><span class="sxs-lookup"><span data-stu-id="cb15f-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="cb15f-108">Kształt jest opisana przez <xref:System.Windows.Media.GeometryGroup> oraz dwóch <xref:System.Windows.Media.EllipseGeometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="cb15f-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="cb15f-109">Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej rysowania za pomocą <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="cb15f-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="cb15f-110"><xref:System.Windows.Media.GeometryDrawing> Jest wyświetlana przy użyciu <xref:System.Windows.Media.ImageDrawing> i <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="cb15f-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="cb15f-111">Na poniższej ilustracji przedstawiono wynikowe <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="cb15f-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="cb15f-112">![GeometryDrawing dwie elipsy](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="cb15f-112">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="cb15f-113">Do utworzenia bardziej złożonych rysunki, można połączyć wiele obiektów rysowania w jednym złożonego rysowania za pomocą <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="cb15f-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb15f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb15f-114">See also</span></span>
- <xref:System.Windows.Media.DrawingGroup>
- [<span data-ttu-id="cb15f-115">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="cb15f-115">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="cb15f-116">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="cb15f-116">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="cb15f-117">Tworzenie złożonego rysunku</span><span class="sxs-lookup"><span data-stu-id="cb15f-117">Create a Composite Drawing</span></span>](how-to-create-a-composite-drawing.md)
