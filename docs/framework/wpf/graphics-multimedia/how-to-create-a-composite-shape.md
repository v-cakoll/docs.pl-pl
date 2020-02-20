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
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452100"
---
# <a name="how-to-create-a-composite-shape"></a>Jak utworzyć kształt złożony
Ten przykład pokazuje, jak tworzyć kształty złożone przy użyciu obiektów <xref:System.Windows.Media.Geometry> i wyświetlać je za pomocą elementu <xref:System.Windows.Shapes.Path>. W poniższym przykładzie <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>i <xref:System.Windows.Media.RectangleGeometry> są używane z <xref:System.Windows.Media.GeometryGroup> do tworzenia kształtu złożonego. Geometrie są następnie rysowane przy użyciu elementu <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Na poniższej ilustracji przedstawiono kształt utworzony w poprzednim przykładzie.  
  
 ![Złożona Geometria utworzona przy użyciu elementu geometrycznego](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Złożona Geometria  
  
 Bardziej złożone kształty, takie jak wielokąty i kształty z zakrzywionymi segmentami, można utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry>. Przykład przedstawiający sposób tworzenia kształtu przy użyciu <xref:System.Windows.Media.PathGeometry>można znaleźć w temacie [Tworzenie kształtu przy użyciu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  Chociaż ten przykład renderuje kształt na ekranie przy użyciu elementu <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Media.Geometry> obiekty mogą być również używane do opisywania zawartości <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>. Mogą być również używane do przycinania i testowania trafień.  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).
