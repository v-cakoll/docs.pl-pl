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
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929611"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Malowanie obrazami, rysowaniem i Visual
W tym temacie opisano, jak <xref:System.Windows.Media.ImageBrush>używać <xref:System.Windows.Media.DrawingBrush>obiektów, <xref:System.Windows.Media.VisualBrush> i do malowania obszaru <xref:System.Windows.Media.Visual>za pomocą obrazu, a <xref:System.Windows.Media.Drawing>lub.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z różnymi typami pędzli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i ich podstawowymi funkcjami. Aby zapoznać się z wprowadzeniem, zobacz [Omówienie pędzli WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Maluj obszar za pomocą obrazu  
 Maluje obszar <xref:System.Windows.Media.ImageSource>za pomocą. <xref:System.Windows.Media.ImageBrush> Najbardziej typowym typem <xref:System.Windows.Media.ImageSource> do użycia <xref:System.Windows.Media.ImageBrush> z a <xref:System.Windows.Media.Imaging.BitmapImage>jest, który opisuje mapę bitową. Możesz użyć <xref:System.Windows.Media.DrawingImage> do malowania <xref:System.Windows.Media.Drawing> przy użyciu obiektu, ale <xref:System.Windows.Media.DrawingBrush> jest to prostsze do użycia. Aby uzyskać więcej informacji <xref:System.Windows.Media.ImageSource> na temat obiektów, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).  
  
 Aby malować przy użyciu <xref:System.Windows.Media.ImageBrush>programu, <xref:System.Windows.Media.Imaging.BitmapImage> Utwórz i użyj go do załadowania zawartości mapy bitowej. Następnie użyj <xref:System.Windows.Media.Imaging.BitmapImage> , aby <xref:System.Windows.Media.ImageBrush.ImageSource%2A> ustawić właściwość <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> Na koniec Zastosuj do obiektu, który chcesz malować.  W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programie można również <xref:System.Windows.Media.ImageBrush.ImageSource%2A> ustawić właściwość na <xref:System.Windows.Media.ImageBrush> ścieżkę obrazu do załadowania.  
  
 Podobnie jak <xref:System.Windows.Media.Brush> w przypadku wszystkich <xref:System.Windows.Media.ImageBrush> obiektów, może służyć do malowania obiektów, takich jak kształty, panele, kontrolki i tekst. Na poniższej ilustracji przedstawiono niektóre efekty, które można osiągnąć przy użyciu <xref:System.Windows.Media.ImageBrush>.  
  
 ![Przykłady danych wyjściowych ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Obiekty rysowane przez ImageBrush  
  
 Domyślnie <xref:System.Windows.Media.ImageBrush> rozciąga swój obraz, aby całkowicie wypełnić obszar malowany, prawdopodobnie zniekształcanie obrazu, jeśli obszar malowany ma inny współczynnik proporcji niż obraz. To zachowanie <xref:System.Windows.Media.TileBrush.Stretch%2A> można zmienić, zmieniając właściwość z <xref:System.Windows.Media.Stretch.Fill> wartości domyślnej na <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>, lub <xref:System.Windows.Media.Stretch.UniformToFill>. Ponieważ <xref:System.Windows.Media.ImageBrush> jest<xref:System.Windows.Media.TileBrush>typem, można określić dokładnie sposób wypełnienia przez pędzel obrazu obszaru wyjściowego, a nawet tworzyć wzorce. Aby uzyskać więcej informacji o <xref:System.Windows.Media.TileBrush> funkcjach zaawansowanych, zobacz [Omówienie funkcji TileBrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Przykład: Malowanie obiektu za pomocą obrazu mapy bitowej  
 Poniższy przykład używa <xref:System.Windows.Media.ImageBrush> do <xref:System.Windows.Controls.Panel.Background%2A> malowania <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Maluj obszar za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> umożliwia malowanie obszaru za pomocą kształtów, tekstu, obrazów i wideo. Kształty wewnątrz pędzla rysowania mogą być namalowane przy użyciu pełnego koloru, gradientu, obrazu, a <xref:System.Windows.Media.DrawingBrush>nawet innego. Na poniższej ilustracji przedstawiono niektóre zastosowania a <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Przykłady danych wyjściowych DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Obiekty rysowane przez DrawingBrush  
  
 Maluje obszar <xref:System.Windows.Media.Drawing> z obiektem. <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing> Obiekt opisuje widoczną zawartość, na przykład kształt, mapę bitową, wideo lub wiersz tekstu. Różne typy rysunków opisują różne typy zawartości. Poniżej znajduje się lista różnych typów obiektów rysowania.  
  
- <xref:System.Windows.Media.GeometryDrawing>— Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>— Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>— Rysuje tekst.  
  
- <xref:System.Windows.Media.VideoDrawing>— Odtwarza plik dźwiękowy lub wideo.  
  
- <xref:System.Windows.Media.DrawingGroup>— Rysuje inne rysunki. Użyj grupy rysowania, aby połączyć inne rysunki w pojedynczy rysunek złożony.  
  
 Aby uzyskać więcej informacji <xref:System.Windows.Media.Drawing> na temat obiektów, zobacz [Omówienie obiektów rysowania](drawing-objects-overview.md).  
  
 Podobnie jak <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush> , rozciąga<xref:System.Windows.Media.DrawingBrush.Drawing%2A> się w celu wypełnienia jego obszaru wyjściowego. To zachowanie można zastąpić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość z domyślnego <xref:System.Windows.Media.Stretch.Fill>ustawienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Przykład: Malowanie obiektu za pomocą rysowania  
 Poniższy przykład pokazuje, jak malować obiekt z rysowaniem trzech wielokropek. A <xref:System.Windows.Media.GeometryDrawing> służy do opisywania elipsy.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Maluj obszar za pomocą Visual  
 Najbardziej wszechstronne i zaawansowane dla wszystkich pędzli, <xref:System.Windows.Media.VisualBrush> malują obszar <xref:System.Windows.Media.Visual>z. A <xref:System.Windows.Media.Visual> jest typem graficznym niskiego poziomu, który służy jako element nadrzędny wielu przydatnych składników graficznych. <xref:System.Windows.Window>Na przykład <xref:System.Windows.FrameworkElement>,, i <xref:System.Windows.Controls.Control> klasy są wszystkie typy <xref:System.Windows.Media.Visual> obiektów. Za pomocą [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , można malować obszary z niemal dowolnymi obiektami graficznymi. <xref:System.Windows.Media.VisualBrush>  
  
> [!NOTE]
> Chociaż <xref:System.Windows.Media.VisualBrush> jest <xref:System.Windows.Media.VisualBrush.Visual%2A> `null`typem obiektu, nie można go zamrozić (tylko do odczytu), gdy jego właściwość jest ustawiona na wartość inną niż. <xref:System.Windows.Freezable>  
  
 Istnieją dwa sposoby określania <xref:System.Windows.Media.VisualBrush.Visual%2A> zawartości. <xref:System.Windows.Media.VisualBrush>  
  
- Utwórz nowy <xref:System.Windows.Media.Visual> i użyj go do <xref:System.Windows.Media.VisualBrush.Visual%2A> ustawienia właściwości <xref:System.Windows.Media.VisualBrush>. Aby zapoznać się z przykładem [, zobacz przykład: Maluj obiekt z sekcją wizualizacji](#examplevisualbrush1) poniżej.  
  
- Użyj istniejącego <xref:System.Windows.Media.Visual>, który tworzy zduplikowany obraz obiektu docelowego <xref:System.Windows.Media.Visual>. Następnie można użyć <xref:System.Windows.Media.VisualBrush> do tworzenia interesujących efektów, takich jak odbicie i powiększanie. Aby zapoznać się z przykładem [, zobacz przykład: Utwórz sekcję odbicia](#examplevisualbrush2) .  
  
 Gdy definiujesz <xref:System.Windows.Media.VisualBrush.Visual%2A> nowy <xref:System.Windows.Media.VisualBrush> dla a, który <xref:System.Windows.Media.Visual> jest <xref:System.Windows.UIElement> (na przykład <xref:System.Windows.UIElement> panel lub kontrolka), system <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> układu jest uruchamiany na i jego elementach podrzędnych, gdy właściwość jest ustawiona na `true`. Jednak główny <xref:System.Windows.UIElement> jest głównie odizolowany od reszty systemu: style i układ zewnętrzny nie permeate tej granicy. W związku z tym należy jawnie określić rozmiar elementu głównego <xref:System.Windows.UIElement>, ponieważ jego jedynym elementem nadrzędnym <xref:System.Windows.Media.VisualBrush> jest, a w związku z tym nie może on automatycznie zmieniać rozmiaru do rysowanego obszaru. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]układu w, zobacz [Układ](../advanced/layout.md).  
  
 Podobnie <xref:System.Windows.Media.ImageBrush> jak <xref:System.Windows.Media.DrawingBrush>i ,<xref:System.Windows.Media.VisualBrush> rozciąga swoją zawartość w celu wypełnienia jej obszaru wyjściowego. To zachowanie można zastąpić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość z domyślnego <xref:System.Windows.Media.Stretch.Fill>ustawienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Przykład: Maluj obiekt za pomocą wizualizacji  
 W poniższym przykładzie kilka kontrolek i panel są używane do malowania prostokąta.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Przykład: Tworzenie odbicia  
 W poprzednim przykładzie pokazano, jak utworzyć nowy <xref:System.Windows.Media.Visual> do użycia jako tło. Możesz również użyć, <xref:System.Windows.Media.VisualBrush> aby wyświetlić istniejącą wizualizację. Ta funkcja umożliwia tworzenie interesujących efektów wizualnych, takich jak odbicie i powiększenia. Poniższy przykład używa <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia <xref:System.Windows.Controls.Border> zawierającego kilka elementów. Na poniższej ilustracji przedstawiono dane wyjściowe generowane przez ten przykład.  
  
 ![Odbicie odbitego obiektu wizualnego](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odbicie odbitego obiektu wizualnego  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Aby uzyskać dodatkowe przykłady pokazujące, jak powiększać fragmenty ekranu i jak tworzyć odbicia, zobacz [przykład VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Funkcje TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> są typami <xref:System.Windows.Media.TileBrush> obiektów. <xref:System.Windows.Media.TileBrush>obiekty zapewniają znaczną kontrolę nad tym, jak obszar jest malowany obrazem, rysunkiem lub wizualizacją. Na przykład zamiast malowania obszaru za pomocą pojedynczego rozciąganego obrazu można malować obszar z serii kafelków obrazu, które tworzą wzorzec.  
  
 <xref:System.Windows.Media.TileBrush> Ma trzy składniki podstawowe: zawartość, kafelki i obszar danych wyjściowych.  
  
 ![Elementy TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki obiektu TileBrush z jednym kafelkiem  
  
 ![Składniki sąsiadującego obiektu TileBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki obiektu TileBrush z wieloma kafelkami  
  
 Aby uzyskać więcej informacji o funkcjach <xref:System.Windows.Media.TileBrush> rozmieszczania obiektów, zobacz [Omówienie obiektu TileBrush](tilebrush-overview.md).  
  
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
- [Przykład ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [Przykład VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
