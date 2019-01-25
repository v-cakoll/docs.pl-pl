---
title: 'Instrukcje: Zachowaj format obrazu użytego jako tło'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: f8133ac4fcd01e08f41861b7a441e9ff1325f6ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698326"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Instrukcje: Zachowaj format obrazu użytego jako tło
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość <xref:System.Windows.Media.ImageBrush> Aby zachować współczynnik proporcji obrazu.  
  
 Domyślnie, gdy używasz <xref:System.Windows.Media.ImageBrush> można malować obszar, jego zawartość zostanie rozciągnięty w celu całkowitego wypełnienia obszaru wyjściowego. Jeśli obszar danych wyjściowych i obraz, który ma różnych współczynnikach proporcji, obraz, który jest zniekształcony to rozciągając.  
  
 Aby <xref:System.Windows.Media.ImageBrush> współczynnik proporcji jego obrazu, ustaw <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch <xref:System.Windows.Media.ImageBrush> obiekty do malowania dwoma prostokątami. Każdego prostokąta wynosi 300 x 150 pikseli i każdy z nich zawiera obraz 300 przez 300 pikseli. <xref:System.Windows.Media.TileBrush.Stretch%2A> Pędzla pierwszy zostaje ustalona <xref:System.Windows.Media.Stretch.Uniform>i <xref:System.Windows.Media.TileBrush.Stretch%2A> drugi pędzla zostaje ustalona <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe pierwszy pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![ImageBrush za pomocą jednolitego rozciąganie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Następna ilustracja przedstawia dane wyjściowe drugi pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![ImageBrush z rozciągania typu UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Należy pamiętać, że <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość zachowuje się tak samo dla siebie <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, aby uzyskać <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> , a druga <xref:System.Windows.Media.TileBrush> obiekty, zobacz [malowanie obrazami, rysowaniem i Visual](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Należy zauważyć, że, mimo że <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość pojawia się, aby określić sposób, w jaki <xref:System.Windows.Media.TileBrush> zawartość zostanie rozciągnięty w celu dopasowania jej obszaru danych wyjściowych, faktycznie określa sposób, w jaki <xref:System.Windows.Media.TileBrush> zawartości odcinkach w celu wypełnienia jego podstawowy Kafelek. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush>.  
  
 Ten przykład kodu jest częścią większego przykładu, który jest udostępniany dla <xref:System.Windows.Media.ImageBrush> klasy. Aby uzyskać pełny przykład, zobacz [przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.TileBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
