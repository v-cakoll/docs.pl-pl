---
title: Jak użyć rysowania jako źródła obrazu
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 7da8a2a594b0562667aaf417d736159d98818a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562293"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Jak użyć rysowania jako źródła obrazu
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> dla <xref:System.Windows.Controls.Image> formantu. Aby wyświetlić <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Controls.Image> kontrolować, użyj <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> formantu <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwości do rysunku mają być wyświetlane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu, aby wyświetlić <xref:System.Windows.Media.GeometryDrawing>. Ten przykład generuje następujące wyniki:  
  
 ![GeometryDrawing zawierający dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Rysowanie obrazu z użyciem elementu ImageDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze, atrybut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
