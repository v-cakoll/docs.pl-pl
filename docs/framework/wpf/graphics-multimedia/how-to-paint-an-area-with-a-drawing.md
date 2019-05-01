---
title: 'Instrukcje: Maluj obszar za pomocą rysowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010088"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>Instrukcje: Maluj obszar za pomocą rysowania
Ten przykład pokazuje, jak malować obszar za pomocą rysowania. Maluj obszar za pomocą rysowania, należy użyć <xref:System.Windows.Media.DrawingBrush> oraz jednego lub więcej <xref:System.Windows.Media.Drawing> obiektów.   W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingBrush> namalować obiektu za pomocą rysowania dwie elipsy.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 Poniższa ilustracja przedstawia przykładowe dane wyjściowe.  
  
 ![Dane wyjściowe z DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (Środek kształt jest białe powodów opisanych w [Kontroluj wypełnienie kształtu złożonego](how-to-control-the-fill-of-a-composite-shape.md).)  
  
 Ustawiając <xref:System.Windows.Media.DrawingBrush> obiektu <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości, można utworzyć powtarzające się wzorca. Poniższy przykład umożliwia malowanie obiektu z wzorcem utworzone na podstawie rysunku dwie elipsy.  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono fragmentacji <xref:System.Windows.Media.DrawingBrush> danych wyjściowych.  
  
 ![Sąsiadująco w danych wyjściowych z DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 Aby uzyskać więcej informacji na temat rysowania pędzle zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md). Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](drawing-objects-overview.md).
