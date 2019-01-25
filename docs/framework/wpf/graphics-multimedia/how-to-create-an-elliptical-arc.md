---
title: 'Instrukcje: Utwórz łuk eliptyczny'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: 4f4461f778e2c86adb3932edf8435ca75b3b5e98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679568"
---
# <a name="how-to-create-an-elliptical-arc"></a>Instrukcje: Utwórz łuk eliptyczny
Ten przykład przedstawia sposób rysowania łuk eliptyczny. Aby utworzyć łuk eliptyczny, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.ArcSegment> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach łuk eliptyczny jest rysowana od (10,100) do (200,100). Łuk <xref:System.Windows.Media.ArcSegment.Size%2A> 100, 50 pikseli niezależnych od urządzenia, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stopni <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ustawienie `true`, a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 [xaml]  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można też rysować łuk eliptyczny przez jawnie przy użyciu tagów obiekt. Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 W tym przykładzie jest częścią większego przykładu. Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie krzywej Beziera drugiego stopnia](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
- [Tworzenie krzywej Beziera trzeciego stopnia](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
