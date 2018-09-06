---
title: Jak narysować kształt zamknięty przy użyciu elementu wielobocznego
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 89c78877e196e803f6b4139ffcfa2b4def1a07d7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873039"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="b6b28-102">Jak narysować kształt zamknięty przy użyciu elementu wielobocznego</span><span class="sxs-lookup"><span data-stu-id="b6b28-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="b6b28-103">W tym przykładzie pokazano, jak narysować kształt zamknięty przy użyciu <xref:System.Windows.Shapes.Polygon> elementu.</span><span class="sxs-lookup"><span data-stu-id="b6b28-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="b6b28-104">Aby narysować kształt zamknięty, należy utworzyć <xref:System.Windows.Shapes.Polygon> element i użyj jej <xref:System.Windows.Shapes.Polygon.Points%2A> właściwości w celu określenia wierzchołków kształtu.</span><span class="sxs-lookup"><span data-stu-id="b6b28-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="b6b28-105">Wiersz jest automatycznie pobierane łączącej punkty imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="b6b28-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="b6b28-106">Ponadto określ <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, lub obu.</span><span class="sxs-lookup"><span data-stu-id="b6b28-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6b28-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6b28-107">Example</span></span>  
 <span data-ttu-id="b6b28-108">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], prawidłowej składni dla punktów znajduje się lista rozdzielonych przecinkami x - i współrzędne y pary rozdzielonych spacjami.</span><span class="sxs-lookup"><span data-stu-id="b6b28-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="b6b28-109">Chociaż w przykładzie użyto <xref:System.Windows.Controls.Canvas> aby zawierają wielokąty, można użyć elementów wielokąta (i wszystkie inne elementy kształtu) ze wszystkimi <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> , która obsługuje zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="b6b28-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="b6b28-110">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="b6b28-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>
