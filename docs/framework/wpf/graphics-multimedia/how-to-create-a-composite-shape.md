---
title: Jak utworzyć kształt złożony
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: 6bb2a8a32938682af52343b971b840dbed16bcef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559975"
---
# <a name="how-to-create-a-composite-shape"></a>Jak utworzyć kształt złożony
W tym przykładzie przedstawiono sposób tworzenia złożonych kształtów za pomocą <xref:System.Windows.Media.Geometry> obiekty i wyświetlać je za pomocą <xref:System.Windows.Shapes.Path> elementu. W poniższym przykładzie <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.RectangleGeometry> są używane z <xref:System.Windows.Media.GeometryGroup> do tworzenia złożonych kształtu. Mają geometrię są rysowane przy użyciu <xref:System.Windows.Shapes.Path> elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie kształtu.  
  
 ![Złożona geometria utworzona przy użyciu obiektu GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Złożone typy geometryczne  
  
 Kształtów bardziej złożonych, takie jak wielokątów i kształty z segmentów krzywych może zostać utworzony przy użyciu <xref:System.Windows.Media.PathGeometry>. Na przykład pokazujący sposób tworzenia kształtu przy użyciu <xref:System.Windows.Media.PathGeometry>, zobacz [tworzenie kształtu przy użyciu PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  Mimo że w tym przykładzie powoduje kształtu do ekranu przy użyciu <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> obiektów może również służyć do opisania zawartości <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>. Mogą one również służyć do wycinka i testowania trafień.  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).
