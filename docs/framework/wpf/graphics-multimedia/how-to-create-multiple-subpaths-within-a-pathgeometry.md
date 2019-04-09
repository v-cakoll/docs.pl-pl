---
title: 'Instrukcje: Tworzenie wielu podścieżek w obrębie elementu PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111751"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Instrukcje: Tworzenie wielu podścieżek w obrębie elementu PathGeometry
W tym przykładzie pokazano, jak utworzyć wiele podścieżek w <xref:System.Windows.Media.PathGeometry>. Aby utworzyć wiele podścieżek, należy utworzyć <xref:System.Windows.Media.PathFigure> dla podrzędnej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie ścieżki podrzędne, każdy z nich trójkąt.  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 Poniższy przykład pokazuje, jak utworzyć wiele podścieżek przy użyciu <xref:System.Windows.Shapes.Path> i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu składni. Każdy `M` przykład tworzy dwie ścieżki podrzędne, że każdy Rysowanie trójkąt tworzy nowy podrzędną.  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.)  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Geometria](geometry-overview.md)
