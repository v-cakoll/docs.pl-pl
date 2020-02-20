---
title: Jak narysować elipsę na okręgu
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452925"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Jak narysować elipsę na okręgu
Ten przykład pokazuje, jak rysować wielokropek i okręgi przy użyciu elementu <xref:System.Windows.Shapes.Ellipse>. Aby narysować wielokropek, Utwórz element <xref:System.Windows.Shapes.Ellipse> i określ jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A>. Użyj właściwości <xref:System.Windows.Shapes.Shape.Fill%2A>, aby określić <xref:System.Windows.Media.Brush> używany do malowania wnętrza wielokropka. Użyj właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A>, aby określić <xref:System.Windows.Media.Brush> używany do malowania konturu elipsy. Właściwość <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> określa grubość konturu elipsy.  
  
 Aby narysować okrąg, <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> elementu <xref:System.Windows.Shapes.Ellipse> być równe siebie.  
  
 Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Ellipse> elementy w <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Chociaż w tym przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierać wielokropek, można użyć elementów wielokropka (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługującym zawartość nietekstową.  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Przykładowe elementy kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
