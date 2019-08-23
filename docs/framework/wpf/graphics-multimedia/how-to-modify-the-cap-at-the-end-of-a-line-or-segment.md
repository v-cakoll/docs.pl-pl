---
title: 'Instrukcje: Modyfikowanie zakończenia na końcu linii lub segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916132"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Instrukcje: Modyfikowanie zakończenia na końcu linii lub segmentu
Ten przykład pokazuje, jak zmodyfikować kształt na początku lub na końcu otwartego <xref:System.Windows.Shapes.Shape> elementu. Aby zmienić zakończenie na początku otwartego <xref:System.Windows.Shapes.Shape>, użyj jego <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> właściwości. Aby zmienić zakończenie na końcu otwartego <xref:System.Windows.Shapes.Shape>, użyj jego <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> właściwości. Aby wyświetlić dostępne wersaliki, zobacz <xref:System.Windows.Media.PenLineCap> Wyliczenie.  
  
> [!NOTE]
> Ta właściwość ma wpływ tylko na otwarty kształt, taki jak <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>lub otwarty <xref:System.Windows.Shapes.Path> element.  
  
 Poniższy przykład rysuje cztery <xref:System.Windows.Shapes.Polyline> elementy i używa różnego zestawu kształtów na końcach każdego z nich.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
