---
title: 'Instrukcje: Tworzenie GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: c3312802b4a623afc10b620dbe2159d2c52a41a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646230"
---
# <a name="how-to-create-a-geometrydrawing"></a>Instrukcje: Tworzenie GeometryDrawing
W tym przykładzie pokazano, jak utworzyć i wyświetlić <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> pozwala na tworzenie kształt z wypełnieniem lecz konspektu, kojarząc <xref:System.Windows.Media.Pen> i <xref:System.Windows.Media.Brush> z <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Opisujący strukturę kształtu <xref:System.Windows.Media.GeometryDrawing.Brush%2A> opisuje wypełnienie kształtu i <xref:System.Windows.Media.GeometryDrawing.Pen%2A> opisuje kontur figury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.GeometryDrawing> do renderowania kształtu. Kształt jest opisana przez <xref:System.Windows.Media.GeometryGroup> oraz dwóch <xref:System.Windows.Media.EllipseGeometry> obiektów. Wewnątrz kształtu jest malowany <xref:System.Windows.Media.LinearGradientBrush> i konturu jej rysowania za pomocą <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Jest wyświetlana przy użyciu <xref:System.Windows.Media.ImageDrawing> i <xref:System.Windows.Controls.Image> elementu.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono wynikowe <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Do utworzenia bardziej złożonych rysunki, można połączyć wiele obiektów rysowania w jednym złożonego rysowania za pomocą <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.DrawingGroup>
- [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [Tworzenie złożonego rysunku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
