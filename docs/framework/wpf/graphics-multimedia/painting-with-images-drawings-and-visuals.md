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
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186922"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Malowanie obrazami, rysowaniem i Visual
W tym temacie <xref:System.Windows.Media.ImageBrush>opisano <xref:System.Windows.Media.DrawingBrush>sposób <xref:System.Windows.Media.VisualBrush> używania programu , a <xref:System.Windows.Media.Drawing>obiekty do <xref:System.Windows.Media.Visual>malowania obszaru obrazem, a lub .  

<a name="prereqs"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] z różnymi typami pędzli zapewnia i ich podstawowe funkcje. Aby uzyskać wprowadzenie, zobacz [WPF Brushes Omówienie](wpf-brushes-overview.md).  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>Maluj obszar za pomocą obrazu  
 Malowanie <xref:System.Windows.Media.ImageBrush> obszaru za <xref:System.Windows.Media.ImageSource>pomocą pliku . Najczęstszym typem <xref:System.Windows.Media.ImageSource> używanego <xref:System.Windows.Media.ImageBrush> z <xref:System.Windows.Media.Imaging.BitmapImage>an jest , który opisuje grafikę bitmapową. Można użyć <xref:System.Windows.Media.DrawingImage> a do <xref:System.Windows.Media.Drawing> malowania za pomocą obiektu, <xref:System.Windows.Media.DrawingBrush> ale zamiast tego łatwiej jest użyć. Aby uzyskać <xref:System.Windows.Media.ImageSource> więcej informacji o obiektach, zobacz [Omówienie obrazowania](imaging-overview.md).  
  
 Aby malować <xref:System.Windows.Media.ImageBrush>za <xref:System.Windows.Media.Imaging.BitmapImage> pomocą programu , utwórz i użyj jej do załadowania zawartości mapy bitowej. Następnie użyj, <xref:System.Windows.Media.Imaging.BitmapImage> aby <xref:System.Windows.Media.ImageBrush.ImageSource%2A> ustawić właściwość . <xref:System.Windows.Media.ImageBrush> Na koniec zastosuj <xref:System.Windows.Media.ImageBrush> do obiektu, który chcesz malować.  W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programze można również <xref:System.Windows.Media.ImageBrush.ImageSource%2A> po <xref:System.Windows.Media.ImageBrush> prostu ustawić właściwość ze ścieżką obrazu do załadowania.  
  
 Podobnie <xref:System.Windows.Media.Brush> jak wszystkie <xref:System.Windows.Media.ImageBrush> obiekty, an może być używany do malowania obiektów, takich jak kształty, panele, formanty i tekst. Na poniższej ilustracji przedstawiono pewne <xref:System.Windows.Media.ImageBrush>efekty, które można osiągnąć za pomocą pliku .  
  
 ![Przykłady danych wyjściowych imageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Obiekty malowane przez ImageBrush  
  
 Domyślnie obraz <xref:System.Windows.Media.ImageBrush> rozciąga obraz, aby całkowicie wypełnić malowany obszar, co może zniekształcać obraz, jeśli malowany obszar ma inny współczynnik proporcji niż obraz. To zachowanie <xref:System.Windows.Media.TileBrush.Stretch%2A> można zmienić, zmieniając właściwość <xref:System.Windows.Media.Stretch.Fill> <xref:System.Windows.Media.Stretch.None>z <xref:System.Windows.Media.Stretch.Uniform>jej <xref:System.Windows.Media.Stretch.UniformToFill>domyślnej wartości na , lub . Ponieważ <xref:System.Windows.Media.ImageBrush> jest to <xref:System.Windows.Media.TileBrush>typ , można określić dokładnie, w jaki sposób pędzel obrazu wypełnia obszar wyjściowy, a nawet tworzy szyki. Aby uzyskać więcej <xref:System.Windows.Media.TileBrush> informacji na temat zaawansowanych funkcji, zobacz [Omówienie kafetki.](tilebrush-overview.md)  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Przykład: Malowanie obiektu obrazem bitmapowym  
 W poniższym przykładzie <xref:System.Windows.Media.ImageBrush> użyto do malowania <xref:System.Windows.Controls.Panel.Background%2A> pliku <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>Maluj obszar za pomocą rysowania  
 A <xref:System.Windows.Media.DrawingBrush> umożliwia malowanie obszaru kształtami, tekstem, obrazami i filmami. Kształty wewnątrz pędzla rysunkowego mogą same być malowane jednolitym <xref:System.Windows.Media.DrawingBrush>kolorem, gradientem, obrazem lub nawet innym . Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.DrawingBrush>niektóre zastosowania pliku .  
  
 ![Przykłady danych wyjściowych drawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Obiekty malowane pędzlem drawingbrush  
  
 A <xref:System.Windows.Media.DrawingBrush> maluje obszar <xref:System.Windows.Media.Drawing> za pomocą obiektu. Obiekt <xref:System.Windows.Media.Drawing> opisuje widoczną zawartość, taką jak kształt, mapa bitowa, wideo lub wiersz tekstu. Różne typy rysunków opisują różne typy zawartości. Poniżej znajduje się lista różnych typów obiektów rysunkowych.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>– Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Rysuje tekst.  
  
- <xref:System.Windows.Media.VideoDrawing>– Odtwarza plik audio lub wideo.  
  
- <xref:System.Windows.Media.DrawingGroup>– Rysuje inne rysunki. Grupa rysunków służy do łączenia innych rysunków w pojedynczy rysunek złożony.  
  
 Aby uzyskać <xref:System.Windows.Media.Drawing> więcej informacji o obiektach, zobacz [Omówienie obiektów rysunkowych](drawing-objects-overview.md).  
  
 Jak <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> rozciąga się, <xref:System.Windows.Media.DrawingBrush.Drawing%2A> aby wypełnić swój obszar wyjściowy. To zachowanie można zastąpić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość z <xref:System.Windows.Media.Stretch.Fill>domyślnego ustawienia . Aby uzyskać więcej <xref:System.Windows.Media.TileBrush.Stretch%2A> informacji, zobacz właściwość.  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>Przykład: Malowanie obiektu rysunkiem  
 W poniższym przykładzie pokazano, jak malować obiekt rysunkiem trzech elips. A <xref:System.Windows.Media.GeometryDrawing> służy do opisywania elips.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>Maluj obszar za pomocą Visual  
 Najbardziej wszechstronny i potężny ze wszystkich <xref:System.Windows.Media.VisualBrush> szczotek, farby obszar z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.Visual> jest niskopoziomowym typem graficznym, który służy jako element nadrzędny wielu przydatnych komponentów graficznych. Na przykład <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>i <xref:System.Windows.Controls.Control> klasy są <xref:System.Windows.Media.Visual> wszystkie typy obiektów. Za <xref:System.Windows.Media.VisualBrush>pomocą programu można malować [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obszary niemal dowolnym obiektem graficznym.  
  
> [!NOTE]
> Chociaż <xref:System.Windows.Media.VisualBrush> jest typem <xref:System.Windows.Freezable> obiektu, nie można go zamrozić (tylko do odczytu), gdy jego <xref:System.Windows.Media.VisualBrush.Visual%2A> właściwość jest ustawiona na wartość inną niż `null`.  
  
 Istnieją dwa sposoby <xref:System.Windows.Media.VisualBrush.Visual%2A> określania <xref:System.Windows.Media.VisualBrush>zawartości pliku .  
  
- Utwórz <xref:System.Windows.Media.Visual> nowy i użyj <xref:System.Windows.Media.VisualBrush.Visual%2A> go, <xref:System.Windows.Media.VisualBrush>aby ustawić właściwość programu . Na przykład zobacz [Przykład: Maluj obiekt za pomocą następującej](#examplevisualbrush1) sekcji Visual.  
  
- Użyj istniejącego <xref:System.Windows.Media.Visual>, który tworzy zduplikowany obraz obiektu docelowego <xref:System.Windows.Media.Visual>. Następnie można użyć <xref:System.Windows.Media.VisualBrush> do tworzenia ciekawych efektów, takich jak odbicie i powiększenie. Na przykład zobacz [Przykład: Tworzenie odbicia](#examplevisualbrush2) sekcji.  
  
 Po zdefiniowaniu <xref:System.Windows.Media.VisualBrush.Visual%2A> nowego <xref:System.Windows.Media.VisualBrush> fora <xref:System.Windows.Media.Visual> i <xref:System.Windows.UIElement> jest to (na przykład panel lub <xref:System.Windows.UIElement> formant), system <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> układu działa `true`na i jego elementy podrzędne, gdy właściwość jest ustawiona na . Jednak katalog <xref:System.Windows.UIElement> główny jest zasadniczo odizolowany od reszty systemu: style i układ zewnętrzny nie może przenikać tej granicy. W związku z tym należy jawnie <xref:System.Windows.UIElement>określić rozmiar katalogu <xref:System.Windows.Media.VisualBrush> głównego , ponieważ jego jedynym elementem nadrzędnym jest i dlatego nie może automatycznie rozmiar się do obszaru malowane. Aby uzyskać więcej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]informacji o układzie w obszarze , zobacz [Układ](../advanced/layout.md).  
  
 Podobnie <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>jak <xref:System.Windows.Media.VisualBrush> i , rozciąga swoją zawartość, aby wypełnić swój obszar wyjściowy. To zachowanie można zastąpić, zmieniając <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwość z <xref:System.Windows.Media.Stretch.Fill>domyślnego ustawienia . Aby uzyskać więcej <xref:System.Windows.Media.TileBrush.Stretch%2A> informacji, zobacz właściwość.  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>Przykład: Malowanie obiektu wizualizacją  
 W poniższym przykładzie kilka formantów i panel są używane do malowania prostokąta.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>Przykład: Tworzenie odbicia  
 W poprzednim przykładzie pokazano, jak <xref:System.Windows.Media.Visual> utworzyć nowy do użycia jako tło. Można również użyć <xref:System.Windows.Media.VisualBrush> a do wyświetlenia istniejącej wizualizacji; ta funkcja umożliwia tworzenie interesujących efektów wizualnych, takich jak odbicia i powiększenie. W poniższym przykładzie <xref:System.Windows.Media.VisualBrush> użyto do <xref:System.Windows.Controls.Border> utworzenia odbicia a, który zawiera kilka elementów. Na poniższej ilustracji przedstawiono dane wyjściowe, które w tym przykładzie produkuje.  
  
 ![Odbity obiekt wizualny](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odbity obiekt wizualny  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Aby uzyskać dodatkowe przykłady, które pokazują, jak powiększać fragmenty ekranu i jak tworzyć odbicia, zobacz [Przykład wizualny pędzla](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>Funkcje tileBrush  
 <xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.DrawingBrush>, i <xref:System.Windows.Media.VisualBrush> są <xref:System.Windows.Media.TileBrush> typami obiektów. <xref:System.Windows.Media.TileBrush>obiekty zapewniają dużą kontrolę nad tym, jak obszar jest malowany obrazem, rysunkiem lub wizualizacją. Na przykład zamiast malować obszar pojedynczym rozciągniętym obrazem, można namalować obszar serią kafelków obrazów, które tworzą wzór.  
  
 A <xref:System.Windows.Media.TileBrush> ma trzy podstawowe składniki: zawartość, kafelki i obszar wyjściowy.  
  
 ![Elementy tileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Składniki tileBrush z pojedynczą płytką  
  
 ![Składniki płytki wyłożonej kafelkamiBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Składniki tileBrush z wieloma płytkami  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Media.TileBrush> temat funkcji kafli obiektów, zobacz [Przegląd Kafebrytki](tilebrush-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush — przegląd](tilebrush-overview.md)
- [Pędzle WPF — przegląd](wpf-brushes-overview.md)
- [Obrazowanie — przegląd](imaging-overview.md)
- [Przegląd Rysowanie obiektów](drawing-objects-overview.md)
- [Maska nieprzezroczystości — przegląd](opacity-masks-overview.md)
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
- [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Przykład pędzla Wizualnego](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
