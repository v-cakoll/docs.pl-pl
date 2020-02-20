---
title: Jak utworzyć krzywą Beziera drugiego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452074"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Jak utworzyć krzywą Beziera drugiego stopnia
Ten przykład pokazuje, jak utworzyć krzywą Beziera kwadratu.  Aby utworzyć krzywą Beziera kwadratu, użyj klas <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>i <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach krzywa Beziera kwadratu jest rysowana od (10 100) do (300 100). Krzywa ma punkt kontrolny (200 200).  
  
 formatu  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można użyć składni atrybutów do opisania ścieżki.  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 formatu  
  
 (Należy zauważyć, że ta składnia atrybutu w rzeczywistości tworzy <xref:System.Windows.Media.StreamGeometry>, a jaśniejszą wersję wagi <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz stronę [składnia znaczników ścieżki](path-markup-syntax.md) .)  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można również narysować krzywą Beziera kwadratowego przy użyciu składni elementu obiektu. Poniżej znajduje się odpowiednik powyższego przykładu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md)
- [Tworzenie krzywej Beziera trzeciego stopnia](how-to-create-a-cubic-bezier-curve.md)
