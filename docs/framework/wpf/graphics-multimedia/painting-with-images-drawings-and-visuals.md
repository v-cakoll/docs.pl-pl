---
title: Malowanie obrazami, rysowaniem i Visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: abb5733ed54ea430ba161db5ea2dcb33e99298ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566915"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Malowanie obrazami, rysowaniem i Visual
W tym temacie opisano sposób użycia <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> obiektów namalować obszar wraz z obrazem <xref:System.Windows.Media.Drawing>, lub <xref:System.Windows.Media.Visual>.  
    
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy zapoznać się z różnymi typami pędzli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia i ich funkcje podstawowe. Aby obejrzeć wprowadzenie, zobacz [omówienie pędzle WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Maluj obszar za pomocą obrazu  
 <xref:System.Windows.Media.ImageBrush> Rysują obszar o <xref:System.Windows.Media.ImageSource>. Najczęściej spotykanym typem z <xref:System.Windows.Media.ImageSource> do użycia z <xref:System.Windows.Media.ImageBrush> jest <xref:System.Windows.Media.Imaging.BitmapImage>, która opisuje grafiki mapy bitowej. Można użyć <xref:System.Windows.Media.DrawingImage> namalować przy użyciu <xref:System.Windows.Media.Drawing> obiekt, ale jej użycie jest łatwiejsze <xref:System.Windows.Media.DrawingBrush> zamiast tego. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageSource> obiekty, zobacz [Imaging omówienie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
 Aby malować <xref:System.Windows.Media.ImageBrush>, Utwórz <xref:System.Windows.Media.Imaging.BitmapImage> i używać go do załadowania zawartości bitmapy. Następnie należy użyć <xref:System.Windows.Media.Imaging.BitmapImage> można ustawić <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwość <xref:System.Windows.Media.ImageBrush>. Na koniec zastosować <xref:System.Windows.Media.ImageBrush> do obiektu malowania.  W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można także ustawić <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwość <xref:System.Windows.Media.ImageBrush> ze ścieżką do załadowania obrazu.  
  
 Takich jak wszystkie <xref:System.Windows.Media.Brush> obiektów, <xref:System.Windows.Media.ImageBrush> może służyć do malowania obiekty, takie jak kształtów, paneli kontrolek i tekst. Na poniższej ilustracji przedstawiono niektóre efekty, które mogą zostać osiągnięty przy <xref:System.Windows.Media.ImageBrush>.  
  
 ![Przykładowe dane wyjściowe ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Obiekty przy użyciu obiektu ImageBrush  
  
 Domyślnie <xref:System.Windows.Media.ImageBrush> odcinkach jego obrazu, aby wypełnić obszaru są rysowane, prawdopodobnie zakłócenia obrazu, jeśli malowanego obszaru ma inny współczynnik proporcji niż obraz. To zachowanie można zmienić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości z wartość domyślną <xref:System.Windows.Media.Stretch.Fill> do <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, lub <xref:System.Windows.Media.Stretch.UniformToFill>. Ponieważ <xref:System.Windows.Media.ImageBrush> jest typem <xref:System.Windows.Media.TileBrush>, można określić dokładnie, jak pędzla obrazu wypełnia obszaru wyjściowego i nawet utworzyć wzorce. Aby uzyskać więcej informacji o zaawansowanych <xref:System.Windows.Media.TileBrush> funkcji, zobacz [omówienie TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Przykład: Malowanie obiektu z obrazu mapy bitowej  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush> namalować <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Maluj obszar za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> umożliwia malowanie obszar o kształtów, tekst, obrazy i wideo. Kształty wewnątrz pędzla do rysowania może się zostać narysowany z pełnego koloru, gradientu, obrazu, lub nawet innej <xref:System.Windows.Media.DrawingBrush>. Poniższa ilustracja przedstawia niektóre zastosowania <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Przykładowe dane wyjściowe pędzla](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Obiekty rysowane przez DrawingBrush  
  
 A <xref:System.Windows.Media.DrawingBrush> rysują obszar o <xref:System.Windows.Media.Drawing> obiektu. A <xref:System.Windows.Media.Drawing> obiektu opisuje widocznej zawartości, takich jak kształtu, mapy bitowej, wideo lub wiersza tekstu. Różne typy rysunki opis różnych typów zawartości. Poniżej znajduje się lista różnych typów obiektów rysowania.  
  
-   <xref:System.Windows.Media.GeometryDrawing> — Rysuje kształt.  
  
-   <xref:System.Windows.Media.ImageDrawing> — Rysuje obraz.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> — Rysuje tekst.  
  
-   <xref:System.Windows.Media.VideoDrawing> — Odtwarza plik audio i wideo.  
  
-   <xref:System.Windows.Media.DrawingGroup> — Rysuje inne rysunki. Użyj grupy rysunku, aby połączyć inne rysunki w jeden złożonego.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysunku](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
 Podobnie jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> rozciąga się jego <xref:System.Windows.Media.DrawingBrush.Drawing%2A> do wypełnienia jej obszaru wyjściowego. To zachowanie można przesłonić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość z ustawień domyślnych <xref:System.Windows.Media.Stretch.Fill>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Przykład: Malowanie obiektu z rysunkiem  
 Poniższy przykład pokazuje, jak namalować obiektu z Rysowanie elips trzy. A <xref:System.Windows.Media.GeometryDrawing> jest używany do opisu wielokropek.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Maluj obszar za pomocą Visual  
 Elastyczne i wydajne pędzli <xref:System.Windows.Media.VisualBrush> rysują obszar o <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> jest typem graficznego niskiego poziomu, który służy jako element nadrzędny elementu wiele składników graficznego przydatne. Na przykład <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, i <xref:System.Windows.Controls.Control> klasy są wszystkie typy <xref:System.Windows.Media.Visual> obiektów. Przy użyciu <xref:System.Windows.Media.VisualBrush>, można malować obszarów z niemal dowolnego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektu graficznego.  
  
> [!NOTE]
>  Mimo że <xref:System.Windows.Media.VisualBrush> jest typem <xref:System.Windows.Freezable> obiektu, nie można zablokować (tylko do odczytu) po jego <xref:System.Windows.Media.VisualBrush.Visual%2A> wartość właściwości jest równa wartości innych niż `null`.  
  
 Istnieją dwa sposoby określania <xref:System.Windows.Media.VisualBrush.Visual%2A> zawartości <xref:System.Windows.Media.VisualBrush>.  
  
-   Utwórz nową <xref:System.Windows.Media.Visual> i użyj jej do ustawienia <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość <xref:System.Windows.Media.VisualBrush>. Na przykład zobacz [przykład: malowanie obiektu z obiektu Visual](#examplevisualbrush1) sekcji.  
  
-   Użyj istniejącego <xref:System.Windows.Media.Visual>, która tworzy obraz zduplikowanych docelowych <xref:System.Windows.Media.Visual>. Następnie można użyć <xref:System.Windows.Media.VisualBrush> utworzyć interesujące efekty, takie jak odbicia i powiększenia. Na przykład zobacz [przykład: tworzenie odbicie](#examplevisualbrush2) sekcji.  
  
 Podczas definiowania nowej <xref:System.Windows.Media.VisualBrush.Visual%2A> dla <xref:System.Windows.Media.VisualBrush> i <xref:System.Windows.Media.Visual> jest <xref:System.Windows.UIElement> (na przykład panelu lub sterowania), system układu działa na <xref:System.Windows.UIElement> i jego elementów podrzędnych podczas <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> właściwość jest ustawiona na `true`. Jednak głównego <xref:System.Windows.UIElement> są zasadniczo odseparowane od pozostałej części systemu: style i układ zewnętrzne nie mogą przenikać przez tę granicę. W związku z tym należy jawnie określić rozmiar głównego <xref:System.Windows.UIElement>, ponieważ jego obiekt nadrzędny tylko <xref:System.Windows.Media.VisualBrush> i dlatego jego nie może automatycznie zmienia swój rozmiar do obszaru są rysowane. Aby uzyskać więcej informacji o układzie w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md).  
  
 Podobnie jak <xref:System.Windows.Media.ImageBrush> i <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> rozciąga się jej zawartość w celu wypełnienia jej obszaru wyjściowego. To zachowanie można przesłonić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość z ustawień domyślnych <xref:System.Windows.Media.Stretch.Fill>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Przykład: Malowanie obiektu z obiektu Visual  
 W poniższym przykładzie kilka formantów i panelu są używane do rysowania prostokąta.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Przykład: Tworzenie odbicie  
 Poprzednim przykładzie pokazano, jak utworzyć nową <xref:System.Windows.Media.Visual> do użycia jako tło. Można również użyć <xref:System.Windows.Media.VisualBrush> Aby wyświetlić istniejące visual; ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia. W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia z <xref:System.Windows.Controls.Border> zawiera wiele elementów. Na poniższej ilustracji przedstawiono dane wyjściowe, który spowoduje utworzenie w tym przykładzie.  
  
 ![Obiekt wizualny odzwierciedlone A](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Obiekt Visual odbite  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Aby uzyskać dodatkowe przykłady sposobu Powiększ fragmenty ekranu oraz do tworzenia odbicia, zobacz [próbki VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Funkcje TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> typów <xref:System.Windows.Media.TileBrush> obiektów. <xref:System.Windows.Media.TileBrush> udostępnia obiekty z dużym stopniem kontrolę nad jak obszar jest rysowane przy użyciu obrazu, rysunku lub visual. Na przykład zamiast tylko malowanie obszar o jeden obraz rozciągnięty, można malować obszar o serię kafelków obrazu, tworzące wzorzec.  
  
 A <xref:System.Windows.Media.TileBrush> ma trzy główne składniki: zawartość, Kafelki i do obszaru wyjściowego.  
  
 ![Składniki TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki TileBrush z jednego kafelka  
  
 ![Składniki sąsiadującym TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki TileBrush z wielu kafelków  
  
 Aby uzyskać więcej informacji o funkcjach kafelków <xref:System.Windows.Media.TileBrush> obiekty, zobacz [omówienie TileBrush](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 <xref:System.Windows.Media.TileBrush>  
 [TileBrush — przegląd](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [Pędzle WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)  
 [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Maska nieprzezroczystości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/opacity-masks-overview.md)  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Przykładowe ImageBrush](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [Przykładowe VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049)
