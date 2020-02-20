---
title: Jak narysować prostokąt
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452938"
---
# <a name="how-to-draw-a-rectangle"></a>Jak narysować prostokąt
Ten przykład pokazuje, jak narysować prostokąt przy użyciu elementu <xref:System.Windows.Shapes.Rectangle>.  
  
 Aby narysować prostokąt, Utwórz element <xref:System.Windows.Shapes.Rectangle> i określ jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>. Aby malować wewnątrz prostokąta, ustaw jego <xref:System.Windows.Shapes.Shape.Fill%2A>. Aby nadać prostokątowi konspekt, użyj jego właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.  
  
 Aby nadać prostokątom Zaokrąglone rogi, określ opcjonalne <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> właściwości. Właściwości <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> i <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> ustawiają promienie osi x i y wielokropka, która jest używana do zaokrąglania rogów prostokąta.  
  
 W poniższym przykładzie dwa elementy <xref:System.Windows.Shapes.Rectangle> są rysowane w <xref:System.Windows.Controls.Canvas>. Pierwszy prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wewnątrz. Drugi prostokąt ma <xref:System.Windows.Media.Brushes.Blue%2A> wnętrze, <xref:System.Windows.Media.Brushes.Black%2A> Konspekt i zaokrąglone rogi.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierać prostokąty, można użyć elementów prostokąta (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control>, które obsługują zawartość inną niż tekst. W rzeczywistości prostokąty są szczególnie przydatne do udostępniania tła dla części paneli <xref:System.Windows.Controls.Grid>. Aby zapoznać się z przykładem, zobacz sekcję [Omówienie tabeli](../advanced/table-overview.md).  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Rectangle>
- [Przykładowe elementy kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
- [Omówienie tabel](../advanced/table-overview.md)
