---
title: Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186834"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Jak ustawić rozmiar sąsiadujących kafelków dla TileBrush

W tym przykładzie pokazano, jak <xref:System.Windows.Media.TileBrush>ustawić rozmiar kafelka dla pliku . Domyślnie tworzy <xref:System.Windows.Media.TileBrush> pojedynczy kafelek, który całkowicie wypełnia obszar, który malujesz. To zachowanie można zastąpić, <xref:System.Windows.Media.TileBrush.Viewport%2A> ustawiając <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> właściwości i.

Właściwość <xref:System.Windows.Media.TileBrush.Viewport%2A> określa rozmiar kafelka <xref:System.Windows.Media.TileBrush>dla . Domyślnie wartość <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości jest względem rozmiaru obszaru malowanego. Aby <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwość określała bezwzględny rozmiar <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> kafelka, ustaw właściwość na <xref:System.Windows.Media.BrushMappingMode.Absolute>.

## <a name="example"></a>Przykład

W poniższym przykładzie <xref:System.Windows.Media.ImageBrush>użyto <xref:System.Windows.Media.TileBrush>, typu , do malowania prostokąta kafelkami. W przykładzie ustawia każdy kafelek na 50 procent przez 50 procent obszaru wyjściowego (prostokąt). W rezultacie prostokąt jest malowany czterema projekcjami obrazu.

Na poniższej ilustracji przedstawiono dane wyjściowe, które daje przykład:

![Prostokąt z czterema wiśniami demonstrującymi układanie za pomocą pędzla obrazu.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

W <xref:System.Windows.Media.ImageBrush>następnym przykładzie tworzy <xref:System.Windows.Media.TileBrush.Viewport%2A> `0,0,25,25` , <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> ustawia <xref:System.Windows.Media.BrushMappingMode.Absolute>jego do i jego do , i używa go do malowania innego prostokąta. W rezultacie pędzel tworzy płytki o szerokości 25 pikseli i wysokości 25 pikseli.

Na poniższej ilustracji przedstawiono dane wyjściowe, które daje przykład:

![Prostokąt z czterdziestu ośmiu wiśni demonstrujących płytki wyłożone kafelkamiBrush z Viewport.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

Powyższe przykłady są częścią większej próbki. Aby uzyskać pełną próbkę, zobacz [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).

Chociaż w tym <xref:System.Windows.Media.ImageBrush> przykładzie <xref:System.Windows.Media.TileBrush.Viewport%2A> używa <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> klasy, i właściwości <xref:System.Windows.Media.TileBrush> zachowują się identycznie <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>dla innych obiektów, czyli dla i . Aby uzyskać <xref:System.Windows.Media.ImageBrush> więcej informacji <xref:System.Windows.Media.TileBrush> o i innych obiektach, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.TileBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Tworzenie różnych wzorów kafelkowych z użyciem elementu TileBrush](how-to-create-different-tile-patterns-with-a-tilebrush.md)
