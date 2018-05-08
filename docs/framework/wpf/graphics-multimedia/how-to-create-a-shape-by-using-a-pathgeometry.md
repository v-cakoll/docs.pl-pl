---
title: Jak utworzyć kształt używając PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: 6c77844b054dd89a0c3f3cbecd0725968df9ae71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Jak utworzyć kształt używając PathGeometry
W tym przykładzie pokazano, jak utworzyć kształtu przy użyciu <xref:System.Windows.Media.PathGeometry> klasy. <xref:System.Windows.Media.PathGeometry> obiekty składają się z co najmniej jeden <xref:System.Windows.Media.PathFigure> obiektów; każda <xref:System.Windows.Media.PathFigure> reprezentuje różne "rysunek" lub kształtu. Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiekty, każdy reprezentuje połączony fragment rysunku lub kształtu. Segment typy <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, i <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.PathGeometry> utworzyć trójkąt. <xref:System.Windows.Media.PathGeometry> Jest wyświetlany za pomocą <xref:System.Windows.Shapes.Path> elementu.  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie kształtu.  
  
 ![Obiekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Trójkąt utworzone za pomocą PathGeometry  
  
 W poprzednim przykładzie pokazano, jak utworzyć stosunkowo proste kształt trójkąta. A <xref:System.Windows.Media.PathGeometry> może również służyć do tworzenia bardziej złożonych kształtów, w tym łuki i krzywych. Przykłady można znaleźć [utworzyć łuku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [tworzenie sześcienny krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), i [tworzenie kwadratową krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Przykładowe mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989)
