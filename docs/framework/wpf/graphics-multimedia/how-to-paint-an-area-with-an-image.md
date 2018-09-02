---
title: Jak malować obszar za pomocą obrazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 5899531291c22ada76213905d0f2ca6944fcbba7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408023"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Jak malować obszar za pomocą obrazu
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ImageBrush> klasy Maluj obszar za pomocą obrazu. <xref:System.Windows.Media.ImageBrush> Wyświetla pojedynczy obraz, który jest określony przez jego <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład farby <xref:System.Windows.Controls.Control.Background%2A> przycisku przy użyciu <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Domyślnie <xref:System.Windows.Media.ImageBrush> rozciąga obraz do całkowitego wypełnienia malowanego obszaru. W powyższym przykładzie obraz jest rozciągany tak, wypełnienie przycisku, prawdopodobnie zakłócanie obrazu. To zachowanie można kontrolować przez ustawienie <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość <xref:System.Windows.Media.TileBrush> do <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill>, co powoduje, że pędzla zachować współczynnik proporcji obrazu.  
  
 Jeśli ustawisz <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości <xref:System.Windows.Media.ImageBrush>, możesz utworzyć powtarzające się wzorca. Poniższy przykład umożliwia malowanie przycisk za pomocą wzorca, który jest tworzony z obrazu.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> klasy, zobacz [malowanie obrazami, rysowaniem i Visual](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Ten przykład kodu jest częścią większego przykładu, który jest udostępniany dla <xref:System.Windows.Media.ImageBrush> klasy. Aby uzyskać pełny przykład, zobacz [przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
