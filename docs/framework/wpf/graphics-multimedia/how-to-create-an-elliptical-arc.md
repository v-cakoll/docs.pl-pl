---
title: Jak utworzyć łuk eliptyczny
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453068"
---
# <a name="how-to-create-an-elliptical-arc"></a>Jak utworzyć łuk eliptyczny
Ten przykład pokazuje, jak narysować Łuk eliptyczny. Aby utworzyć Łuk eliptyczny, użyj klas <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>i <xref:System.Windows.Media.ArcSegment>.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach Łuk eliptyczny jest rysowany z (10 100) do (200 100). Łuk ma <xref:System.Windows.Media.ArcSegment.Size%2A> 100 przez 50 pikseli niezależnych od urządzenia, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> z 45 stopni, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ustawienie `true`i <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 formatu  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można użyć składni atrybutów do opisania ścieżki.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 formatu  
  
 (Należy zauważyć, że ta składnia atrybutu w rzeczywistości tworzy <xref:System.Windows.Media.StreamGeometry>, a jaśniejszą wersję wagi <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz stronę [składnia znaczników ścieżki](path-markup-syntax.md) .)  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można również narysować Łuk eliptyczny przez jawne użycie tagów obiektów. Poniżej znajduje się odpowiednik poprzedzającego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Ten przykład jest częścią większego przykładu. Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie krzywej Beziera drugiego stopnia](how-to-create-a-quadratic-bezier-curve.md)
- [Tworzenie krzywej Beziera trzeciego stopnia](how-to-create-a-cubic-bezier-curve.md)
