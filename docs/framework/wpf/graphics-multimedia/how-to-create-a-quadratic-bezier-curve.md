---
title: 'Instrukcje: Tworzenie krzywej Beziera drugiego stopnia'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: a0b2145b4a5bba11186419fe680f2eca41949d6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054572"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Instrukcje: Tworzenie krzywej Beziera drugiego stopnia
W tym przykładzie pokazano, jak utworzyć krzywą Beziera drugiego stopnia.  Aby utworzyć krzywą Beziera drugiego stopnia, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.QuadraticBezierSegment> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach krzywą Beziera drugiego stopnia jest rysowana od (10,100) do (300,100). Krzywa ma punkt kontrolny w (200,200).  
  
 [xaml]  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 [xaml]  
  
 (Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.)  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], może również zwracać krzywą Beziera drugiego stopnia stosowanie składni obiektów. Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md)
- [Tworzenie krzywej Beziera trzeciego stopnia](how-to-create-a-cubic-bezier-curve.md)
