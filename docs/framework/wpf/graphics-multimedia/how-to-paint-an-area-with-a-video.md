---
title: Jak malować obszar za pomocą wideo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: d2ca0f8b70abf6e895ea275d2a47eb4a6dd4bfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-video"></a>Jak malować obszar za pomocą wideo
W tym przykładzie pokazano, jak namalować obszar z nośnika. Jednym ze sposobów Malowanie obszaru z nośnika jest użycie <xref:System.Windows.Controls.MediaElement> razem z <xref:System.Windows.Media.VisualBrush>. Użyj <xref:System.Windows.Controls.MediaElement> do ładowania i odtwarzanie multimediów i użyj jej do ustawienia <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość <xref:System.Windows.Media.VisualBrush>. Następnie można użyć <xref:System.Windows.Media.VisualBrush> namalować obszar o załadowane nośniki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.VisualBrush> namalować <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> formantu o wideo. W tym przykładzie <xref:System.Windows.Controls.MediaElement.IsMuted%2A> właściwość <xref:System.Windows.Controls.MediaElement> do `true` tak, aby generuje Brak dźwięku.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>Przykład  
 Ponieważ <xref:System.Windows.Media.VisualBrush> dziedziczy <xref:System.Windows.Media.TileBrush> klasy, udostępnia kilka metod kafelków. Przez ustawienie <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.VisualBrush> do <xref:System.Windows.Media.TileMode.Tile> i ustawiając jego <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości na wartość mniejszą niż malowanego obszaru, możesz utworzyć wzorzec sąsiadującym.  
  
 Poniższy przykład jest taki sam jak poprzedni przykład, z wyjątkiem <xref:System.Windows.Media.VisualBrush> generuje wzorca z wideo.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Aby uzyskać informacje o sposobie dodawania pliku zawartości, takich jak plik multimedialny do aplikacji, zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md). Podczas dodawania pliku nośnika, należy dodać jako plik zawartości, a nie jako plik zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.VisualBrush>  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush — przegląd](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [Multimedia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
