---
title: 'Instrukcje: Tworzenie kształtu złożonego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: de9f7972c7a51ea623c3630fe62bb48f6109317e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052901"
---
# <a name="how-to-create-a-composite-shape"></a>Instrukcje: Tworzenie kształtu złożonego
W tym przykładzie przedstawiono sposób tworzenia złożonych kształtów za pomocą <xref:System.Windows.Media.Geometry> obiektów i wyświetlać je za pomocą <xref:System.Windows.Shapes.Path> elementu. W poniższym przykładzie <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.RectangleGeometry> są używane wraz z <xref:System.Windows.Media.GeometryGroup> utworzyć kształt złożony. Geometrie są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Poniższa ilustracja przedstawia kształtem utworzona w poprzednim przykładzie.  
  
 ![Złożone typy geometryczne, utworzony za pomocą GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Złożone typy geometryczne  
  
 Bardziej złożonych kształtów, na przykład wielokątów i kształtów za pomocą punkty kontrolne mogą zostać utworzone za pomocą <xref:System.Windows.Media.PathGeometry>. Aby uzyskać przykład pokazujący, jak utworzyć kształt używając <xref:System.Windows.Media.PathGeometry>, zobacz [Utwórz kształt używając PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  Mimo że w tym przykładzie powoduje wyświetlenie kształt na ekranie za pomocą <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> obiektów może również służyć do opisu zawartość <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>. Mogą one również służyć do przycinania i testowania trafień.  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).
