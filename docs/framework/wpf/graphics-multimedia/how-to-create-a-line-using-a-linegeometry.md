---
title: "Jak utworzyć linię używając LineGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acb2c3db2027f8a4e9594212d1f5af9ea1c8a43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="0bdd7-102">Jak utworzyć linię używając LineGeometry</span><span class="sxs-lookup"><span data-stu-id="0bdd7-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="0bdd7-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.LineGeometry> klasy do opisywania wiersza.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="0bdd7-104">A <xref:System.Windows.Media.LineGeometry> jest definiowana za pomocą jego początkowego i końcowego.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bdd7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bdd7-105">Example</span></span>  
 <span data-ttu-id="0bdd7-106">Poniższy przykład przedstawia sposób tworzenia i renderowania <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="0bdd7-107">A <xref:System.Windows.Shapes.Path> element jest używany do renderowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="0bdd7-108">Ponieważ wiersz nie ma żadnych obszaru <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Shape.Fill%2A> nie jest określona; zamiast tego <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości są używane.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="0bdd7-109">![Obiekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="0bdd7-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="0bdd7-110">Obiekt LineGeometry rysowane z (10,20) (100,130)</span><span class="sxs-lookup"><span data-stu-id="0bdd7-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="0bdd7-111">Inne klasy proste geometrii obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="0bdd7-112">Te mają geometrię, a także bardziej złożonych z nich, można również tworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0bdd7-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="0bdd7-113">Aby uzyskać więcej informacji, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0bdd7-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdd7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bdd7-114">See Also</span></span>  
 [<span data-ttu-id="0bdd7-115">Omówienie geometrii</span><span class="sxs-lookup"><span data-stu-id="0bdd7-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="0bdd7-116">Tworzenie złożonego kształtu</span><span class="sxs-lookup"><span data-stu-id="0bdd7-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="0bdd7-117">Tworzenie za pomocą PathGeometry kształtu</span><span class="sxs-lookup"><span data-stu-id="0bdd7-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
