---
title: "Jak zachować format obrazu użytego jako tło"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9716d91a99eb79e38b729424389b2962d1eb6b1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Jak zachować format obrazu użytego jako tło
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość <xref:System.Windows.Media.ImageBrush> w celu zachowania proporcji obrazu.  
  
 Domyślnie, gdy używasz <xref:System.Windows.Media.ImageBrush> namalować obszar jego zawartość zostanie rozciągnięty w celu wypełnia całkowicie obszaru wyjściowego. Jeśli do obszaru wyjściowego i obrazu różnych współczynników proporcji, obraz jest zniekształcony przez ten rozciąganie.  
  
 Aby <xref:System.Windows.Media.ImageBrush> współczynnik proporcji jego obrazu, ustaw <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch <xref:System.Windows.Media.ImageBrush> obiektów namalować dwóch prostokątów. Każdy prostokąt jest 300 pikseli 150 i każdy z nich zawiera obraz pikseli 300 przez 300. <xref:System.Windows.Media.TileBrush.Stretch%2A> Ma ustawioną właściwość pędzla pierwszy <xref:System.Windows.Media.Stretch.Uniform>i <xref:System.Windows.Media.TileBrush.Stretch%2A> ma ustawioną właściwość pędzla drugi <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe pierwszy pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![ImageBrush z Uniform rozciąganie](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Na następnej ilustracji przedstawiono dane wyjściowe drugi pędzla, który ma <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![Obiekt ImageBrush z rozciągania typu UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Należy pamiętać, że <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości zachowuje się tak samo dla siebie <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, aby uzyskać <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> i innych <xref:System.Windows.Media.TileBrush> obiekty, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Należy zauważyć, że, mimo że <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości pojawia się, aby określić sposób <xref:System.Windows.Media.TileBrush> zawartość zostanie rozciągnięty w celu dopasowania jej obszaru danych wyjściowych, faktycznie określa sposób <xref:System.Windows.Media.TileBrush> zawartości odcinkach do wypełnienia jej podstawowy Kafelek. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush>.  
  
 Ten przykładowy kod jest częścią większego przykładu udostępnionego dla <xref:System.Windows.Media.ImageBrush> klasy. Pełny przykład, zobacz [próbki ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.TileBrush>  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
