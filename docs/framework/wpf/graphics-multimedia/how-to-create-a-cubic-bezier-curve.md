---
title: Jak utworzyć krzywą Beziera trzeciego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452113"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Jak utworzyć krzywą Beziera trzeciego stopnia
Ten przykład pokazuje, jak utworzyć wskaźnik krzywej Beziera w postaci sześciennej. Aby utworzyć w sześciennej krzywej Beziera, użyj klas <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>i <xref:System.Windows.Media.BezierSegment>.  Aby wyświetlić wyniki geometryczne, użyj elementu <xref:System.Windows.Shapes.Path> lub użyj go z <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>. W poniższych przykładowych krzywych Beziera jest rysowana od (10, 100) do (300, 100). Krzywa ma punkty kontrolne (100, 0) i (200, 200).  
  
## <a name="example"></a>Przykład  
 formatu  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można użyć skróconej składni znaczników do opisania ścieżki.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 formatu  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można również narysować zakrzywioną krzywą Beziera przy użyciu tagów obiektów. Poniżej znajduje się odpowiednik powyższego przykładu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md)
- [Tworzenie obiektu LineSegment w elemencie PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Tworzenie krzywej Beziera trzeciego stopnia](how-to-create-a-cubic-bezier-curve.md)
- [Tworzenie krzywej Beziera drugiego stopnia](how-to-create-a-quadratic-bezier-curve.md)
