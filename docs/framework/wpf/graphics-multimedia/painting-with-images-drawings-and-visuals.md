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
ms.openlocfilehash: 826c5a0656a9a7e7cff0e96fc6755c5c9c717993
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204201"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Malowanie obrazami, rysowaniem i Visual
W tym temacie opisano sposób użycia <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> obiektów można malować obszar za pomocą obrazu, <xref:System.Windows.Media.Drawing>, lub <xref:System.Windows.Media.Visual>.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z różnymi typami pędzle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia i ich funkcje podstawowe. Aby zapoznać się z wprowadzeniem, zobacz [pędzle WPF — Przegląd](wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Maluj obszar za pomocą obrazu  
 <xref:System.Windows.Media.ImageBrush> Malowanie obszaru za pomocą <xref:System.Windows.Media.ImageSource>. Najczęściej spotykanym typem <xref:System.Windows.Media.ImageSource> za pomocą <xref:System.Windows.Media.ImageBrush> jest <xref:System.Windows.Media.Imaging.BitmapImage>, która opisuje grafiki mapy bitowej. Możesz użyć <xref:System.Windows.Media.DrawingImage> do malowania, za pomocą <xref:System.Windows.Media.Drawing> obiektu, ale jest łatwiejszy w obsłudze <xref:System.Windows.Media.DrawingBrush> zamiast tego. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.ImageSource> obiekty, zobacz [Przegląd obrazowanie](imaging-overview.md).  
  
 Aby malować <xref:System.Windows.Media.ImageBrush>, Utwórz <xref:System.Windows.Media.Imaging.BitmapImage> i użyć go do załadowania zawartości bitmapy. Następnie należy użyć <xref:System.Windows.Media.Imaging.BitmapImage> można ustawić <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwość <xref:System.Windows.Media.ImageBrush>. Na koniec Zastosuj <xref:System.Windows.Media.ImageBrush> obiektowi malowania.  W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], możesz też po prostu ustawić <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwość <xref:System.Windows.Media.ImageBrush> ze ścieżką obrazu do załadowania.  
  
 Podobnie jak wszystkie <xref:System.Windows.Media.Brush> obiektów <xref:System.Windows.Media.ImageBrush> może służyć do malowania obiekty, takie jak kształty, panele, formantów i tekst. Na poniższej ilustracji przedstawiono niektóre efekty, które można osiągnąć za pomocą <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush output examples](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Obiekty przy użyciu obiektu ImageBrush  
  
 Domyślnie <xref:System.Windows.Media.ImageBrush> odcinkach jego obrazu, aby całkowicie wypełnić obszar jest malowane, prawdopodobnie zakłócanie obrazu, jeśli malowanego obszaru ma inny współczynnik proporcji niż obraz. To zachowanie można zmienić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości z jego wartość domyślną <xref:System.Windows.Media.Stretch.Fill> do <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, lub <xref:System.Windows.Media.Stretch.UniformToFill>. Ponieważ <xref:System.Windows.Media.ImageBrush> jest typem <xref:System.Windows.Media.TileBrush>, można określić dokładnie, jak klasa ImageBrush wypełnia obszar danych wyjściowych, a nawet tworzyć wzorców. Aby uzyskać więcej informacji na temat zaawansowana <xref:System.Windows.Media.TileBrush> funkcje, zobacz [TileBrush — Przegląd](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Przykład: Malowanie obiektu przy użyciu obrazu mapy bitowej  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush> namalować <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Maluj obszar za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> umożliwia malowanie obszaru za pomocą kształtów, tekstu, obrazów i filmów wideo. Kształty wewnątrz pędzla mogą sami narysowania za pomocą jednolitego koloru, gradientu, obraz, lub nawet inny <xref:System.Windows.Media.DrawingBrush>. Poniższa ilustracja przedstawia niektóre zastosowań <xref:System.Windows.Media.DrawingBrush>.  
  
 ![DrawingBrush danych wyjściowych przykłady](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Obiekty malowane przez DrawingBrush  
  
 A <xref:System.Windows.Media.DrawingBrush> Malowanie obszaru za pomocą <xref:System.Windows.Media.Drawing> obiektu. A <xref:System.Windows.Media.Drawing> obiekt w tym artykule opisano widoczne zawartości, takiej jak kształt, mapy bitowej, wideo lub wiersza tekstu. Różne rodzaje rysunki opis różnych typów zawartości. Oto lista różne rodzaje Rysowanie obiektów.  
  
-   <xref:System.Windows.Media.GeometryDrawing> — Rysuje kształt.  
  
-   <xref:System.Windows.Media.ImageDrawing> — Rysuje obraz.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> — Rysuje tekst.  
  
-   <xref:System.Windows.Media.VideoDrawing> — Odtwarza plik audio lub wideo.  
  
-   <xref:System.Windows.Media.DrawingGroup> — Rysuje inne rysunki. Aby połączyć inne rysunki w jeden złożony, należy użyć rysowania grupy.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](drawing-objects-overview.md).  
  
 Podobnie jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> rozciąga jego <xref:System.Windows.Media.DrawingBrush.Drawing%2A> do wypełnienia obszaru jego danych wyjściowych. Zachowanie to można zastąpić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości z ustawień domyślnych <xref:System.Windows.Media.Stretch.Fill>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Przykład: Malowanie obiektu za pomocą rysowania  
 Poniższy przykład pokazuje, jak namalować obiektu za pomocą rysowania trzy wielokropek. A <xref:System.Windows.Media.GeometryDrawing> służy do opisywania wielokropek.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Maluj obszar za pomocą Visual  
 Uniwersalna i wydajne pędzli <xref:System.Windows.Media.VisualBrush> Malowanie obszaru za pomocą <xref:System.Windows.Media.Visual>. Element <xref:System.Windows.Media.Visual> jest typem graficzny niskiego poziomu, który służy jako element nadrzędny elementu wiele składników graficzny przydatne. Na przykład <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>, i <xref:System.Windows.Controls.Control> klasy są wszystkie typy <xref:System.Windows.Media.Visual> obiektów. Za pomocą <xref:System.Windows.Media.VisualBrush>, można malować obszarów z niemal dowolnego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektu graficznego.  
  
> [!NOTE]
>  Mimo że <xref:System.Windows.Media.VisualBrush> jest typem <xref:System.Windows.Freezable> obiektu, nie można zablokować (wprowadzić tylko do odczytu) po jego <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwości jest równa wartości innych niż `null`.  
  
 Istnieją dwa sposoby, aby określić <xref:System.Windows.Media.VisualBrush.Visual%2A> zawartości <xref:System.Windows.Media.VisualBrush>.  
  
-   Utwórz nową <xref:System.Windows.Media.Visual> i użyj go, aby ustawić <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość <xref:System.Windows.Media.VisualBrush>. Aby uzyskać przykład, zobacz [przykładu: Malowanie obiektu za pomocą wizualizacji](#examplevisualbrush1) Poniższa sekcja.  
  
-   Użyj istniejącego <xref:System.Windows.Media.Visual>, który tworzy zduplikowane obraz elementu docelowego <xref:System.Windows.Media.Visual>. Następnie można użyć <xref:System.Windows.Media.VisualBrush> do tworzenia efektów interesujące, takie jak odbicia i powiększenia. Aby uzyskać przykład, zobacz [przykładu: Tworzenie odbicia](#examplevisualbrush2) sekcji.  
  
 Podczas definiowania nowej <xref:System.Windows.Media.VisualBrush.Visual%2A> dla <xref:System.Windows.Media.VisualBrush> i <xref:System.Windows.Media.Visual> jest <xref:System.Windows.UIElement> (takich jak panel lub kontrolka), układ jest uruchomiony system <xref:System.Windows.UIElement> i jego elementy podrzędne przy <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> właściwość jest ustawiona na `true`. Jednak główny <xref:System.Windows.UIElement> jest zasadniczo jest odizolowana od reszty systemu: stylów i układu zewnętrznych nie charakteryzują tę granicę. W związku z tym, należy jawnie określić rozmiar głównej <xref:System.Windows.UIElement>, ponieważ jest jedynym nadrzędnego <xref:System.Windows.Media.VisualBrush> i w związku z tym go nie może automatycznie rozmiar samego do obszaru są rysowane. Aby uzyskać więcej informacji na temat układu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], zobacz [układ](../advanced/layout.md).  
  
 Podobnie jak <xref:System.Windows.Media.ImageBrush> i <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> rozciąga jej zawartość w celu wypełnienia obszaru jego danych wyjściowych. Zachowanie to można zastąpić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości z ustawień domyślnych <xref:System.Windows.Media.Stretch.Fill>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Przykład: Malowanie obiektu za pomocą wizualizacji  
 W poniższym przykładzie kilka formantów i panelu są używane do malowania prostokąta.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Przykład: Tworzenie odbicia  
 Poprzednim przykładzie pokazano, jak utworzyć nową <xref:System.Windows.Media.Visual> do użycia jako tło. Można również użyć <xref:System.Windows.Media.VisualBrush> do wyświetlenia istniejącej wizualizacji; ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia. W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenie odbicia <xref:System.Windows.Controls.Border> zawiera wiele elementów. Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.  
  
 ![A odzwierciedlone obiekt wizualny](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odbitych obiekt wizualny  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Aby uzyskać więcej przykładów, które pokazują, jak powiększać części ekranu i Tworzenie odbić, zobacz [przykładowe VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Funkcje TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> typów <xref:System.Windows.Media.TileBrush> obiektów. <xref:System.Windows.Media.TileBrush> obiekty zapewnia dużą kontrolę nad jak obszar jest malowany obrazów, rysowania lub wizualizacji danych. Na przykład zamiast tylko Malowanie obszaru za pomocą pojedynczego obrazu rozciągnięty, można malować obszar za pomocą szeregu Kafelki obrazów, tworzące wzorzec.  
  
 Element <xref:System.Windows.Media.TileBrush> ma trzy główne składniki: zawartość, Kafelki i obszaru wyjściowego.  
  
 ![Składniki TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki TileBrush z jednym kafelkiem  
  
 ![Składniki fragmentacji TileBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki TileBrush o wiele kafelków  
  
 Aby uzyskać więcej informacji o funkcjach fragmentacji <xref:System.Windows.Media.TileBrush> obiekty, zobacz [TileBrush — Przegląd](tilebrush-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush — przegląd](tilebrush-overview.md)
- [Pędzle WPF — przegląd](wpf-brushes-overview.md)
- [Obrazowanie — przegląd](imaging-overview.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Maska nieprzezroczystości — przegląd](opacity-masks-overview.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
- [Przykładowe ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049)
