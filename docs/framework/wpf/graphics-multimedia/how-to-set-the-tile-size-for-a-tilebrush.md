---
title: "Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 484419c05c3d607212ea6d565777cf49cbfdbc19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush
W tym przykładzie pokazano, jak ustawić rozmiar kafelka <xref:System.Windows.Media.TileBrush>. Domyślnie <xref:System.Windows.Media.TileBrush> tworzy pojedynczy fragment, który całkowicie wypełnienia malowanego obszaru. To zachowanie można przesłonić, ustawiając <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości.  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Właściwość określa rozmiar kafelka <xref:System.Windows.Media.TileBrush>. Domyślnie wartość <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość jest określana względem rozmiar obszaru są rysowane. Aby <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości określ rozmiar kafelka bezwzględne, ustaw <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush>, typ <xref:System.Windows.Media.TileBrush>, namalować prostokąt z kafelków. W przykładzie każdego kafelka na 50 procent 50 procent obszaru wyjściowego (prostokąt). W związku z tym prostokąt jest malowany cztery projekcje obrazu.  
  
 Na poniższej ilustracji przedstawiono przykład tworzy dane wyjściowe.
  
 ![Przykład kafelków za pomocą pędzla obrazu](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 W następnym przykładzie jest tworzony <xref:System.Windows.Media.ImageBrush>, ustawia jego <xref:System.Windows.Media.TileBrush.Viewport%2A> do `0,0,25,25` i jego <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> do <xref:System.Windows.Media.BrushMappingMode.Absolute>i używa go do malowania innego prostokąta. W związku z tym pędzla tworzy Kafelki, które mają 25 pikseli szerokości i wysokości 25 pikseli.  
  
 Na poniższej ilustracji przedstawiono przykład tworzy dane wyjściowe.  
  
 ![A sąsiadująco obiekt TileBrush z 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Powyższych przykładach są częścią większego przykładu. Pełny przykład, zobacz [próbki ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Media.ImageBrush> klasy <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości zachowują się tak samo dla pozostałych <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, że dla <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> i innych <xref:System.Windows.Media.TileBrush> obiekty, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.TileBrush>  
 [Malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Utwórz kafelka różnych wzorców z element TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
