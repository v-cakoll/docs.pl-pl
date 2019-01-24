---
title: 'Instrukcje: Narysuj linię'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: 54152b6b68dd453c565afa2ffb23edfe8132a441
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629023"
---
# <a name="how-to-draw-a-line"></a>Instrukcje: Narysuj linię
W tym przykładzie pokazano, jak rysowanie linii za pomocą <xref:System.Windows.Shapes.Line> elementu.  
  
 Aby narysować linię, należy utworzyć <xref:System.Windows.Shapes.Line> elementu. Użyj jego <xref:System.Windows.Shapes.Line.X1%2A> i <xref:System.Windows.Shapes.Line.Y1%2A> właściwości, aby ustawić jej punktu początkowego; i używać jej <xref:System.Windows.Shapes.Line.X2%2A> i <xref:System.Windows.Shapes.Line.Y2%2A> właściwości, aby ustawić jej punkt końcowy. Wreszcie, ustaw jego <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> ponieważ wiersza bez obrysu jest niewidoczne.  
  
 Ustawienie <xref:System.Windows.Shapes.Shape.Fill%2A> element wiersza nie ma wpływu, ponieważ ma nie wewnętrznych.  
  
 Poniższy przykład pobiera trzy wiersze wewnątrz <xref:System.Windows.Controls.Canvas> elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Shapes.Line>
- [Przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037)
