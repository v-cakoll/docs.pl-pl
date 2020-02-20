---
title: Jak narysować linię
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452951"
---
# <a name="how-to-draw-a-line"></a>Jak narysować linię
Ten przykład pokazuje, jak rysować linie przy użyciu elementu <xref:System.Windows.Shapes.Line>.  
  
 Aby narysować linię, Utwórz element <xref:System.Windows.Shapes.Line>. Użyj właściwości <xref:System.Windows.Shapes.Line.X1%2A> i <xref:System.Windows.Shapes.Line.Y1%2A>, aby ustawić punkt początkowy; Aby ustawić swój punkt końcowy, użyj właściwości <xref:System.Windows.Shapes.Line.X2%2A> i <xref:System.Windows.Shapes.Line.Y2%2A>. Na koniec Ustaw <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>, ponieważ linia bez pociągnięcia jest niewidoczna.  
  
 Ustawianie elementu <xref:System.Windows.Shapes.Shape.Fill%2A> dla wiersza nie ma żadnego efektu, ponieważ linia nie ma wnętrza.  
  
 Poniższy przykład rysuje trzy wiersze wewnątrz elementu <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Shapes.Line>
- [Przykładowe elementy kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
