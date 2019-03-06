---
title: 'Instrukcje: Utwórz linię używając LineGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: 6d5d0b413f940a2c7f70e05135ff070c1fe5ba21
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374664"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="cbdb5-102">Instrukcje: Utwórz linię używając LineGeometry</span><span class="sxs-lookup"><span data-stu-id="cbdb5-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="cbdb5-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.LineGeometry> klasę do opisania wiersza.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="cbdb5-104">Element <xref:System.Windows.Media.LineGeometry> jest definiowany przez jego punkt początkowy i końcowy.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbdb5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbdb5-105">Example</span></span>  
 <span data-ttu-id="cbdb5-106">Poniższy przykład pokazuje, jak utworzyć i renderowania <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="cbdb5-107">A <xref:System.Windows.Shapes.Path> element jest używany do renderowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="cbdb5-108">Ponieważ ma bez obszaru <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Shape.Fill%2A> nie jest określona; zamiast tego <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości są używane.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="cbdb5-109">![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="cbdb5-109">![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="cbdb5-110">LineGeometry rysowane z (10,20) (100,130)</span><span class="sxs-lookup"><span data-stu-id="cbdb5-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="cbdb5-111">Inne klasy geometrii proste obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="cbdb5-112">Te geometrii, a także bardziej złożonych te można również utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cbdb5-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="cbdb5-113">Aby uzyskać więcej informacji, zobacz [Przegląd Geometria](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cbdb5-113">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdb5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbdb5-114">See also</span></span>
- [<span data-ttu-id="cbdb5-115">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="cbdb5-115">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="cbdb5-116">Tworzenie kształtu złożonego</span><span class="sxs-lookup"><span data-stu-id="cbdb5-116">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="cbdb5-117">Tworzenie kształtu przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="cbdb5-117">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
