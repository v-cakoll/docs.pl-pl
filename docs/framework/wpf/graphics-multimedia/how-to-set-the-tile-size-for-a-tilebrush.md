---
title: 'Instrukcje: Ustaw rozmiar sąsiadujących kafelków dla TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 4bfc14693f1714206e89ec50128ad62dd239dbee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713567"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Instrukcje: Ustaw rozmiar sąsiadujących kafelków dla TileBrush
W tym przykładzie pokazano, jak Ustaw rozmiar sąsiadujących kafelków dla <xref:System.Windows.Media.TileBrush>. Domyślnie <xref:System.Windows.Media.TileBrush> generuje pojedynczy fragment, który całkowicie wypełnienia malowanego obszaru. Zachowanie to można zastąpić, ustawiając <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości.  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Właściwość określa rozmiar kafelka <xref:System.Windows.Media.TileBrush>. Domyślnie wartość <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość jest określana względem rozmiar obszaru są rysowane. Zapewnienie <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość określać rozmiar fragmentu bezwzględny, ustaw <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwość <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush>, typem <xref:System.Windows.Media.TileBrush>, do malowania prostokąt z kafelków. W przykładzie ustawiono każdego fragmentu do 50 procent o 50% do obszaru wyjściowego (prostokąt). W rezultacie prostokąta jest malowany cztery projekcje obrazu.  
  
 Poniższa ilustracja przedstawia przykład generuje dane wyjściowe.
  
 ![Przykład fragmentacji pędzlem obraz](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 Następny przykład tworzy <xref:System.Windows.Media.ImageBrush>, ustawia jego <xref:System.Windows.Media.TileBrush.Viewport%2A> do `0,0,25,25` i jego <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> do <xref:System.Windows.Media.BrushMappingMode.Absolute>i używa ich do rysowania innego prostokąta. W rezultacie pędzel tworzy Kafelki, które mają 25 pikseli szerokości i wysokości 25 pikseli.  
  
 Poniższa ilustracja przedstawia przykład generuje dane wyjściowe.  
  
 ![A sąsiadująco obiekt TileBrush z 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Powyższych przykładach są częścią większego przykładu. Aby uzyskać pełny przykład, zobacz [przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Media.ImageBrush> klasy <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości zachowują się identycznie dla siebie <xref:System.Windows.Media.TileBrush> obiekty, oznacza to, że dla <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageBrush> , a druga <xref:System.Windows.Media.TileBrush> obiekty, zobacz [malowanie obrazami, rysowaniem i Visual](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.TileBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Tworzenie różnych wzorów kafelkowych z użyciem elementu TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
