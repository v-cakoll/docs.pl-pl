---
title: 'Instrukcje: Definiowanie prostokąta przy użyciu elementu RectangleGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 146ca7017ee38ad5c1065e59662ac441e7bfbfe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075799"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Instrukcje: Definiowanie prostokąta przy użyciu elementu RectangleGeometry
W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Media.RectangleGeometry> klasę do opisania prostokąta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć i renderowania <xref:System.Windows.Media.RectangleGeometry>.  Względne położenie i wymiary prostokąta są definiowane przez <xref:System.Windows.Rect> struktury. Względne położenie jest `50,50` i wysokość i szerokość są `25` tworzenia kwadrat. Wewnętrzne prostokąta jest malowany <xref:System.Windows.Media.Brushes.LemonChiffon%2A> pędzla i jego konspekt jest malowany <xref:System.Windows.Media.Brushes.Black%2A> grubość pociągnięć `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Shapes.Path> element do renderowania <xref:System.Windows.Media.RectangleGeometry>, istnieje wiele sposobów używania <xref:System.Windows.Media.RectangleGeometry> obiektów. Na przykład <xref:System.Windows.Media.RectangleGeometry> może służyć do określania <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> lub <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.  
  
 Inne klasy geometrii proste obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>. Te geometrii, a także bardziej złożonych te można również utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Zobacz także

- [Geometria — przegląd](geometry-overview.md)
- [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md)
- [Tworzenie kształtu przy użyciu elementu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
