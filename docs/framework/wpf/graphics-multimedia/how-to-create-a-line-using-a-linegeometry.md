---
title: 'Instrukcje: Tworzenie linii przy użyciu elementu LineGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: f8c334a54f78aec7af91064a447fd18f23dcfbdc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905206"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Instrukcje: Tworzenie linii przy użyciu elementu LineGeometry
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.LineGeometry> klasę do opisania wiersza. Element <xref:System.Windows.Media.LineGeometry> jest definiowany przez jego punkt początkowy i końcowy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć i renderowania <xref:System.Windows.Media.LineGeometry>.  A <xref:System.Windows.Shapes.Path> element jest używany do renderowania wiersza.  Ponieważ ma bez obszaru <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Shape.Fill%2A> nie jest określona; zamiast tego <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości są używane.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry rysowane z (10,20) (100,130)  
  
 Inne klasy geometrii proste obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>. Te geometrii, a także bardziej złożonych te można również utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>. Aby uzyskać więcej informacji, zobacz [Przegląd Geometria](geometry-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Geometria — przegląd](geometry-overview.md)
- [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md)
- [Tworzenie kształtu przy użyciu elementu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
