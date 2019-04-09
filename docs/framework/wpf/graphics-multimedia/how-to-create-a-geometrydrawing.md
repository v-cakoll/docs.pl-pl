---
title: 'Instrukcje: Tworzenie elementu GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: f5cdcfdb68ad8030bcbd6c689f45a8baddd000e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179793"
---
# <a name="how-to-create-a-geometrydrawing"></a>Instrukcje: Tworzenie elementu GeometryDrawing
W tym przykładzie pokazano, jak utworzyć i wyświetlić <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> pozwala na tworzenie kształt z wypełnieniem lecz konspektu, kojarząc <xref:System.Windows.Media.Pen> i <xref:System.Windows.Media.Brush> z <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Opisujący strukturę kształtu <xref:System.Windows.Media.GeometryDrawing.Brush%2A> opisuje wypełnienie kształtu i <xref:System.Windows.Media.GeometryDrawing.Pen%2A> opisuje kontur figury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> do renderowania kształtu. Kształt jest opisana przez <xref:System.Windows.Media.GeometryGroup> oraz dwóch <xref:System.Windows.Media.EllipseGeometry> obiektów. Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej rysowania za pomocą <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Jest wyświetlana przy użyciu <xref:System.Windows.Media.ImageDrawing> i <xref:System.Windows.Controls.Image> elementu.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono wynikowe <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dwie elipsy](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Do utworzenia bardziej złożonych rysunki, można połączyć wiele obiektów rysowania w jednym złożonego rysowania za pomocą <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingGroup>
- [Przegląd Rysowanie obiektów](drawing-objects-overview.md)
- [Przegląd Geometria](geometry-overview.md)
- [Tworzenie złożonego rysunku](how-to-create-a-composite-drawing.md)
