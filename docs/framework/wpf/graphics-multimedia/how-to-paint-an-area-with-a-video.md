---
title: 'Instrukcje: Malowanie obszaru za pomocą wideo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: be09d1310847cd7214ea795a704c25d994f07b7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921735"
---
# <a name="how-to-paint-an-area-with-a-video"></a>Instrukcje: Malowanie obszaru za pomocą wideo
Ten przykład pokazuje, jak malować obszar za pomocą nośnika. Jednym ze sposobów Maluj obszar za pomocą nośnika jest użycie <xref:System.Windows.Controls.MediaElement> wraz z <xref:System.Windows.Media.VisualBrush>. Użyj <xref:System.Windows.Controls.MediaElement> do ładowania i odtwarzania nośnika i użyj go, aby ustawić <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość <xref:System.Windows.Media.VisualBrush>. Następnie można użyć <xref:System.Windows.Media.VisualBrush> można malować obszar za pomocą załadowane nośniki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.VisualBrush> namalować <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> kontrolki wideo. W tym przykładzie <xref:System.Windows.Controls.MediaElement.IsMuted%2A> właściwość <xref:System.Windows.Controls.MediaElement> do `true` tak, aby generuje Brak dźwięku.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>Przykład  
 Ponieważ <xref:System.Windows.Media.VisualBrush> dziedziczy <xref:System.Windows.Media.TileBrush> klasy, udostępnia kilka metod fragmentacji. Ustawiając <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.VisualBrush> do <xref:System.Windows.Media.TileMode.Tile> i ustawiając jego <xref:System.Windows.Media.TileBrush.Viewport%2A> właściwości na wartość mniejszą niż malowanego obszaru, możesz utworzyć fragmentacji wzorca.  
  
 Poniższy przykład jest identyczny z poprzednim przykładem, chyba że <xref:System.Windows.Media.VisualBrush> generuje wzorca z filmu wideo.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Aby uzyskać informacje dotyczące dodawania pliku zawartości, takich jak plik multimedialny do aplikacji, zobacz [zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md). Po dodaniu pliku nośnika, należy dodać jako pliku zawartości, a nie jako plik zasobów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.VisualBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [TileBrush — przegląd](tilebrush-overview.md)
- [Multimedia — przegląd](multimedia-overview.md)
