---
title: Jak utworzyć kształt używając PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452048"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Jak utworzyć kształt używając PathGeometry
Ten przykład przedstawia sposób tworzenia kształtu przy użyciu klasy <xref:System.Windows.Media.PathGeometry>. obiekty <xref:System.Windows.Media.PathGeometry> składają się z co najmniej jednego obiektu <xref:System.Windows.Media.PathFigure>; Każda <xref:System.Windows.Media.PathFigure> reprezentuje inny "rysunek" lub "kształt". Każda <xref:System.Windows.Media.PathFigure> jest sama składająca się z co najmniej jednego obiektu <xref:System.Windows.Media.PathSegment>, z których każdy reprezentuje podłączoną część rysunku lub kształtu. Typy segmentów obejmują <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>i <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Windows.Media.PathGeometry>, aby utworzyć trójkąt. <xref:System.Windows.Media.PathGeometry> jest wyświetlana przy użyciu elementu <xref:System.Windows.Shapes.Path>.  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Na poniższej ilustracji przedstawiono kształt utworzony w poprzednim przykładzie.  
  
 ![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Trójkąt utworzony przy użyciu elementu PathGeometry  
  
 W poprzednim przykładzie pokazano, jak utworzyć stosunkowo prosty kształt, Trójkąt. <xref:System.Windows.Media.PathGeometry> można również użyć do tworzenia bardziej złożonych kształtów, w tym łuków i krzywych. Aby zapoznać się z przykładami, zobacz [Tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md), [Tworzenie zakrzywionej krzywej Beziera](how-to-create-a-cubic-bezier-curve.md)i [Tworzenie krzywej Beziera kwadratowego](how-to-create-a-quadratic-bezier-curve.md).  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Geometria — przegląd](geometry-overview.md)
- [Przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
