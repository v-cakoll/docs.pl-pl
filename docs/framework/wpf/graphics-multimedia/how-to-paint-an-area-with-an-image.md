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
ms.openlocfilehash: 4efecc3c8083396d4c06d86d9ece01bd584a1c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-an-image"></a>Jak malować obszar za pomocą obrazu
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ImageBrush> klasy namalować obszaru z obrazem. <xref:System.Windows.Media.ImageBrush> Wyświetla pojedynczego obrazu, który jest określony przez jego <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Następujący przykład farby <xref:System.Windows.Controls.Control.Background%2A> przycisku przy użyciu <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Domyślnie <xref:System.Windows.Media.ImageBrush> rozciąga się jego obrazu do całkowitego wypełnienia malowanego obszaru. W poprzednim przykładzie obraz jest rozciągany w celu wypełnienia przycisku, prawdopodobnie zakłócenia obrazu. To zachowanie można kontrolować przez ustawienie <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość <xref:System.Windows.Media.TileBrush> do <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill>, co powoduje, że pędzla do zachowania proporcji obrazu.  
  
 Jeśli ustawisz <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwości <xref:System.Windows.Media.ImageBrush>, można utworzyć identycznych wzorca. Poniższy przykład umożliwia malowanie przycisk za pomocą wzorca, który jest tworzony z obrazu.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> , zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Ten przykładowy kod jest częścią większego przykładu udostępnionego dla <xref:System.Windows.Media.ImageBrush> klasy. Pełny przykład, zobacz [próbki ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
