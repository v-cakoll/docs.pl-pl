---
title: 'Instrukcje: Używanie rysowania jako źródła obrazu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769352"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Instrukcje: Używanie rysowania jako źródła obrazu
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> dla <xref:System.Windows.Controls.Image> kontroli. Do wyświetlenia <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Controls.Image> kontrolować, należy użyć <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> kontrolki <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwości do rysunku, którą chcesz wyświetlić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu, aby wyświetlić <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące wyniki:  
  
 ![GeometryDrawing dwie elipsy](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable.Freeze%2A>
- [Rysowanie obrazu z użyciem elementu ImageDrawing](how-to-draw-an-image-using-imagedrawing.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze, atrybut](../advanced/presentationoptions-freeze-attribute.md)
