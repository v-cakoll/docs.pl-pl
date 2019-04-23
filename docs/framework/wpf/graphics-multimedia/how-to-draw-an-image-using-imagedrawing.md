---
title: 'Instrukcje: Rysowanie obrazu z użyciem elementu ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100161"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Instrukcje: Rysowanie obrazu z użyciem elementu ImageDrawing
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ImageDrawing> do rysowania obrazu. <xref:System.Windows.Media.ImageDrawing> Umożliwia możesz wyświetlić <xref:System.Windows.Media.ImageSource> z <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, lub <xref:System.Windows.Media.Visual>. Aby narysować obrazu, należy utworzyć <xref:System.Windows.Media.ImageDrawing> i ustaw jego <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwości. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Właściwości Określa obraz do rysowania i <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> właściwość określa położenie i rozmiar każdego obrazu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład obejmuje tworzenie złożonego rysunku przy użyciu czterech <xref:System.Windows.Media.ImageDrawing> obiektów. Ten przykład generuje poniższej ilustracji:  
  
 ![Niektóre obiekty DrawingImage](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Cztery ImageDrawing — obiekty  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Na przykład przedstawiający prosty sposób wyświetlania obrazu bez użycia <xref:System.Windows.Media.ImageDrawing>, zobacz [Użyj elementu obrazu](../controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze, atrybut](../advanced/presentationoptions-freeze-attribute.md)
