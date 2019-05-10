---
title: 'Instrukcje: Ustawianie wyrównania elementu TileBrush w poziomie i pionie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
ms.openlocfilehash: e3bfb2b209e40c435c3a321c874dfbd7a9a2fd50
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912374"
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Instrukcje: Ustawianie wyrównania elementu TileBrush w poziomie i pionie
W tym przykładzie pokazano, jak kontrolować wyrównanie poziome i pionowe zawartości we fragmencie. Aby kontrolować wyrównanie poziome i pionowe <xref:System.Windows.Media.TileBrush>, użyj jej <xref:System.Windows.Media.TileBrush.AlignmentX%2A> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwości.  
  
 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwości <xref:System.Windows.Media.TileBrush> są używane podczas jest spełniony jeden z następujących warunków:  
  
- <xref:System.Windows.Media.TileBrush.Stretch%2A> Właściwość <xref:System.Windows.Media.Stretch.Uniform> lub <xref:System.Windows.Media.Stretch.UniformToFill> i <xref:System.Windows.Media.TileBrush.Viewbox%2A> i <xref:System.Windows.Media.TileBrush.Viewport%2A> mają różnych współczynnikach proporcji.  
  
- <xref:System.Windows.Media.TileBrush.Stretch%2A> Właściwość <xref:System.Windows.Media.Stretch.None> i <xref:System.Windows.Media.TileBrush.Viewbox%2A> i <xref:System.Windows.Media.TileBrush.Viewport%2A> mają różne rozmiary.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Wyrównuje zawartość <xref:System.Windows.Media.DrawingBrush>, który jest typem <xref:System.Windows.Media.TileBrush>, do lewego górnego rogu jej Kafelek. Aby wyrównać zawartości, na przykład ustawia <xref:System.Windows.Media.TileBrush.AlignmentX%2A> właściwość <xref:System.Windows.Media.DrawingBrush> do <xref:System.Windows.Media.AlignmentX.Left> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwość <xref:System.Windows.Media.AlignmentY.Top>. Ten przykład generuje następujące dane wyjściowe.  
  
 ![TileBrush z góry&#45;wyrównanie do lewej](./media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
TileBrush z zawartością wyrównany do lewego górnego rogu  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Przykład  
 Następny przykład Wyrównuje zawartość <xref:System.Windows.Media.DrawingBrush> do prawego dolnego rogu jego kafelka, ustawiając <xref:System.Windows.Media.TileBrush.AlignmentX%2A> właściwości <xref:System.Windows.Media.AlignmentX.Right> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwość <xref:System.Windows.Media.AlignmentY.Bottom>. Przykład generuje następujące wyniki.  
  
 ![TileBrush z dołu&#45;kliknij prawym przyciskiem myszy wyrównanie](./media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
TileBrush z zawartością wyrównany do prawego dolnego rogu  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Przykład  
 Następny przykład Wyrównuje zawartość <xref:System.Windows.Media.DrawingBrush> do lewego górnego rogu jego kafelka, ustawiając <xref:System.Windows.Media.TileBrush.AlignmentX%2A> właściwości <xref:System.Windows.Media.AlignmentX.Left> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwość <xref:System.Windows.Media.AlignmentY.Top>. Ustawia również <xref:System.Windows.Media.TileBrush.Viewport%2A> i <xref:System.Windows.Media.TileBrush.TileMode%2A> z <xref:System.Windows.Media.DrawingBrush> do produkcji wzorzec kafelka. Przykład generuje następujące wyniki.  
  
 ![Element TileBrush układu sąsiadującego za pomocą górnej&#45;wyrównanie do lewej](./media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Wzorzec kafelka z zawartością wyrównany do lewej górnej w podstawowy Kafelek  
  
 Najważniejsze funkcje ilustracji abase kafelka, dzięki czemu można zobaczyć, jak jego zawartość jest powiązana. Należy zauważyć, że <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ustawienie nie obowiązuje, ponieważ zawartość <xref:System.Windows.Media.DrawingBrush> nie spełnia całkowicie podstawowy Kafelek w poziomie.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Przykład  
 Ostatnim przykładzie Wyrównuje zawartość sąsiadującej <xref:System.Windows.Media.DrawingBrush> do prawej dolnej jego podstawowy Kafelek, ustawiając <xref:System.Windows.Media.TileBrush.AlignmentX%2A> właściwości <xref:System.Windows.Media.AlignmentX.Right> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwość <xref:System.Windows.Media.AlignmentY.Bottom>. Przykład generuje następujące wyniki.  
  
 ![Element TileBrush układu sąsiadującego za pomocą dolnej&#45;kliknij prawym przyciskiem myszy wyrównanie](./media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Wzorzec kafelka z zawartością wyrównany do prawej dolnej w podstawowy Kafelek  
  
 Ponownie <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ustawienie nie obowiązuje, ponieważ zawartość <xref:System.Windows.Media.DrawingBrush> nie spełnia całkowicie podstawowy Kafelek w poziomie.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 W przykładach użyto <xref:System.Windows.Media.DrawingBrush> obiektów, aby zademonstrować sposób, w jaki <xref:System.Windows.Media.TileBrush.AlignmentX%2A> i <xref:System.Windows.Media.TileBrush.AlignmentY%2A> właściwości są używane. Właściwości te zachowują się identycznie, w przypadku wszystkich pędzli kafelka: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, i <xref:System.Windows.Media.VisualBrush>. Aby uzyskać więcej informacji na temat pędzle kafelka zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.VisualBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
