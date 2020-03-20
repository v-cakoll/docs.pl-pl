---
title: Jak zachować format obrazu użytego jako tło
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186028"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Jak zachować format obrazu użytego jako tło
W tym przykładzie <xref:System.Windows.Media.TileBrush.Stretch%2A> pokazano, <xref:System.Windows.Media.ImageBrush> jak używać właściwości an w celu zachowania proporcji obrazu.  
  
 Domyślnie, gdy używasz <xref:System.Windows.Media.ImageBrush> do malowania obszaru, jego zawartość rozciąga się, aby całkowicie wypełnić obszar wyjściowy. Gdy obszar wyjściowy i obraz mają różne proporcje, obraz jest zniekształcony przez to rozciąganie.  
  
 Aby <xref:System.Windows.Media.ImageBrush> zachować współczynnik proporcji jego obrazu, ustaw <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość na <xref:System.Windows.Media.Stretch.Uniform> lub . <xref:System.Windows.Media.Stretch.UniformToFill>  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch <xref:System.Windows.Media.ImageBrush> obiektów do malowania dwóch prostokątów. Każdy prostokąt ma rozmiar 300 na 150 pikseli i zawiera obraz o proporcjach 300 na 300 pikseli. Właściwość <xref:System.Windows.Media.TileBrush.Stretch%2A> pierwszego pędzla jest <xref:System.Windows.Media.Stretch.Uniform>ustawiona <xref:System.Windows.Media.TileBrush.Stretch%2A> na , a właściwość drugiego pędzla jest ustawiona na <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe pierwszego pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![ImageBrush z równomiernym rozciąganiem](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Na następnej ilustracji przedstawiono dane wyjściowe drugiego pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![ImageBrush z rozciąganiem UniformToFill](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Należy zauważyć, <xref:System.Windows.Media.TileBrush.Stretch%2A> że właściwość zachowuje <xref:System.Windows.Media.TileBrush> się identycznie <xref:System.Windows.Media.DrawingBrush> dla <xref:System.Windows.Media.VisualBrush>innych obiektów, czyli dla i . Aby uzyskać <xref:System.Windows.Media.ImageBrush> więcej informacji <xref:System.Windows.Media.TileBrush> o i innych obiektach, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
 Należy również zauważyć, <xref:System.Windows.Media.TileBrush.Stretch%2A> że chociaż właściwość wydaje się określać, jak <xref:System.Windows.Media.TileBrush> zawartość rozciąga <xref:System.Windows.Media.TileBrush> się, aby dopasować swój obszar wyjściowy, faktycznie określa, jak zawartość rozciąga się, aby wypełnić jego kafelka podstawowego. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush>.  
  
 W tym przykładzie kodu jest częścią większego <xref:System.Windows.Media.ImageBrush> przykładu, który jest dostarczany dla klasy. Aby uzyskać pełną próbkę, zobacz [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.TileBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
