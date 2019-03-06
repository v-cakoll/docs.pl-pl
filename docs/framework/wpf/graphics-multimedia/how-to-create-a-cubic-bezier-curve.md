---
title: 'Instrukcje: Utwórz krzywą Beziera trzeciego stopnia'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: da5472408caf8db92fd025730de48b820397f372
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364570"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Instrukcje: Utwórz krzywą Beziera trzeciego stopnia
W tym przykładzie pokazano, jak utworzyć krzywą Beziera trzeciego stopnia. Aby utworzyć krzywą Beziera trzeciego stopnia, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.BezierSegment> klasy.  Aby wyświetlić wynikowe geometry, użyj <xref:System.Windows.Shapes.Path> elementu, lub korzystać z niej za pomocą <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>. W poniższych przykładach krzywą Beziera trzeciego stopnia jest rysowana od (10, 100) na (300, 100). Krzywa ma punkty kontrolne (100, 0) i (200, 200).  
  
## <a name="example"></a>Przykład  
 [xaml]  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], może użyć znaczników skróconej składni opisujący ścieżkę.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można też rysować krzywą Beziera trzeciego stopnia przy użyciu tagów obiekt. Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md)
- [Tworzenie obiektu LineSegment w elemencie PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Tworzenie krzywej Beziera trzeciego stopnia](how-to-create-a-cubic-bezier-curve.md)
- [Tworzenie krzywej Beziera drugiego stopnia](how-to-create-a-quadratic-bezier-curve.md)
