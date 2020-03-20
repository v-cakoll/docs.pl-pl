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
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186053"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Jak malować obszar za pomocą obrazu
W tym przykładzie <xref:System.Windows.Media.ImageBrush> pokazano, jak używać klasy do malowania obszaru obrazem. Wyświetla <xref:System.Windows.Media.ImageBrush> pojedynczy obraz, który jest <xref:System.Windows.Media.ImageBrush.ImageSource%2A> określony przez jego właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład maluje <xref:System.Windows.Controls.Control.Background%2A> przycisk za <xref:System.Windows.Media.ImageBrush>pomocą .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Domyślnie jego <xref:System.Windows.Media.ImageBrush> obraz jest rozciągany, aby całkowicie wypełnić malowane go miejsce. W poprzednim przykładzie obraz jest rozciągnięty, aby wypełnić przycisk, co może zniekształcić obraz. To zachowanie można kontrolować, <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawiając <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>właściwość <xref:System.Windows.Media.TileBrush> do lub , co powoduje, że pędzel zachowuje proporcje obrazu.  
  
 Jeśli <xref:System.Windows.Media.TileBrush.Viewport%2A> ustawisz <xref:System.Windows.Media.TileBrush.TileMode%2A> i właściwości <xref:System.Windows.Media.ImageBrush>elementu , można utworzyć wzorzec powtarzalny. Poniższy przykład maluje przycisk przy użyciu wzoru, który jest tworzony na podstawie obrazu.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Aby uzyskać więcej <xref:System.Windows.Media.ImageBrush> informacji na temat klasy, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
 W tym przykładzie kodu jest częścią większego <xref:System.Windows.Media.ImageBrush> przykładu, który jest dostarczany dla klasy. Aby uzyskać pełną próbkę, zobacz [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Zobacz też

- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
