---
title: 'Optymalizacja wydajności: Grafika 2D i obrazowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933351"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optymalizacja wydajności: Grafika 2D i obrazowanie
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje szeroką gamę funkcji graficznych 2D i obrazów, które można zoptymalizować pod kątem wymagań aplikacji. Ten temat zawiera informacje o optymalizacji wydajności w tych obszarach.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Rysowanie i kształty  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia zarówno <xref:System.Windows.Media.Drawing> obiekty <xref:System.Windows.Shapes.Shape> , jak i reprezentujące graficzną zawartość rysunku. Jednak obiekty są prostsze konstrukcje niż <xref:System.Windows.Shapes.Shape> obiekty i zapewniają lepszą wydajność. <xref:System.Windows.Media.Drawing>  
  
 A <xref:System.Windows.Shapes.Shape> umożliwia narysowanie graficznego kształtu na ekranie. Ponieważ pochodzą one z <xref:System.Windows.FrameworkElement> klasy, <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz paneli i większości formantów.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje kilka warstw dostępu do usług graficznych i renderowania. Na najwyższej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewniają wiele przydatnych funkcji, takich jak obsługa układu i zdarzeń. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele gotowych do użycia obiektów kształtów. Wszystkie obiekty kształtu dziedziczą z <xref:System.Windows.Shapes.Shape> klasy. Dostępne obiekty kształtu obejmują <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> ,<xref:System.Windows.Shapes.Polyline>,, i <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing>obiekty, z drugiej strony, nie pochodzą od <xref:System.Windows.FrameworkElement> klasy i zapewniają jaśniejszą implementację do renderowania kształtów, obrazów i tekstu.  
  
 Istnieją cztery typy <xref:System.Windows.Media.Drawing> obiektów:  
  
- <xref:System.Windows.Media.GeometryDrawing>Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Rysuje tekst.  
  
- <xref:System.Windows.Media.DrawingGroup>Rysuje inne rysunki. Użyj grupy rysowania, aby połączyć inne rysunki w pojedynczy rysunek złożony.  
  
 <xref:System.Windows.Media.GeometryDrawing> Obiekt służy do renderowania zawartości geometrycznej. Klasa i konkretne klasy, które pochodzą od niej, takie jak <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, i <xref:System.Windows.Media.PathGeometry>zapewniają metodę renderowania grafiki 2D, a także zapewnianie obsługi testowania trafień i przycinania. <xref:System.Windows.Media.Geometry> Obiekty geometryczne mogą służyć do definiowania regionu kontrolki, na przykład lub do definiowania regionu klipu, który ma zostać zastosowany do obrazu. Obiekty geometryczne mogą być prostymi regionami, takimi jak prostokąty i okręgi, lub złożone regiony utworzone na podstawie dwóch lub większej liczby obiektów geometrycznych. Bardziej złożone regiony geometryczne mogą być tworzone przez <xref:System.Windows.Media.PathSegment>łączenie obiektów pochodnych, takich jak <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, i <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na powierzchni <xref:System.Windows.Media.Geometry> Klasa <xref:System.Windows.Shapes.Shape> i Klasa są bardzo podobne. Oba są używane podczas renderowania grafiki 2D i obie mają podobne konkretne klasy, które pochodzą z nich, na przykład <xref:System.Windows.Media.EllipseGeometry> i. <xref:System.Windows.Shapes.Ellipse> Istnieją jednak istotne różnice między tymi dwoma zestawami klas. Dla jednej <xref:System.Windows.Media.Geometry> klasy nie ma niektórych funkcji <xref:System.Windows.Shapes.Shape> klasy, takich jak możliwość rysowania. Aby narysować obiekt geometryczny, należy użyć innej klasy, takiej jak DrawingContext, Drawing lub Path (należy zauważyć, że ścieżka jest kształt), aby wykonać operację rysowania. Właściwości renderowania, takie jak Fill, Stroke i grubość obrysu, znajdują się na klasie, która rysuje obiekt geometryczny, natomiast obiekt Shape zawiera te właściwości. Jednym ze sposobów na uwzględnienie różnic polega na tym, że obiekt geometrii definiuje region, na przykład, a obiekt Shape definiuje region, definiuje, w jaki sposób ten region jest wypełniany i jest wyróżniony oraz uczestniczy w systemie układu.  
  
 Ponieważ <xref:System.Windows.Shapes.Shape> obiekty pochodne <xref:System.Windows.FrameworkElement> od klasy, korzystanie z nich może znacznie zwiększyć użycie pamięci w aplikacji. Jeśli naprawdę nie potrzebujesz <xref:System.Windows.FrameworkElement> funkcji dla zawartości graficznej, rozważ użycie obiektów z jaśniejszą ilością. <xref:System.Windows.Media.Drawing>  
  
 Aby uzyskać więcej informacji <xref:System.Windows.Media.Drawing> na temat obiektów, zobacz [Rysowanie obiektów — Omówienie](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry — obiekty  
 Obiekt jest lekkim <xref:System.Windows.Media.PathGeometry> alternatywą dla tworzenia kształtów geometrycznych. <xref:System.Windows.Media.StreamGeometry> Należy użyć <xref:System.Windows.Media.StreamGeometry> , gdy trzeba opisać złożoną geometrię. <xref:System.Windows.Media.StreamGeometry>jest zoptymalizowany pod kątem obsługi <xref:System.Windows.Media.PathGeometry> wielu obiektów i jest lepszy w porównaniu z użyciem wielu <xref:System.Windows.Media.PathGeometry> pojedynczych obiektów.  
  
 W poniższym przykładzie użyto składni atrybutu w celu utworzenia <xref:System.Windows.Media.StreamGeometry> trójkąta [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Aby uzyskać więcej informacji <xref:System.Windows.Media.StreamGeometry> na temat obiektów, zobacz [Tworzenie kształtu przy użyciu StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Użycie DrawingVisual — obiekty  
 <xref:System.Windows.Media.DrawingVisual> Obiekt jest lekkim klasą rysowania, która jest używana do renderowania kształtów, obrazów lub tekstu. Ta klasa jest uznawana za uproszczoną, ponieważ nie zapewnia obsługi układu ani zdarzeń, co zwiększa jego wydajność. Z tego powodu rysunki są idealnym rozwiązaniem dla tła i clipartów. Aby uzyskać więcej informacji, zobacz [Korzystanie z obiektów użycie DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Obrazy  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Program Imaging zapewnia znaczną poprawę możliwości tworzenia obrazów w poprzednich wersjach systemu Windows. Możliwości tworzenia obrazu, takie jak wyświetlanie mapy bitowej lub używanie obrazu na wspólnej kontrolce, były głównie obsługiwane przez program Microsoft Windows GDI (GDI) lub interfejs programowania aplikacji (API) dla systemu Microsoft Windows. Te interfejsy API zapewniają funkcję obrazu podstawowego, ale nie mają żadnych funkcji, takich jak obsługa rozszerzalności koderów-dekoder i obsługa obrazów o wysokiej wierności. Interfejs API programu WPF Imaging został przeprojektowany w celu pokonania wad GDI i GDI+ oraz udostępnienie nowego zestawu interfejsów API do wyświetlania i używania obrazów w aplikacjach.  
  
 W przypadku korzystania z obrazów należy wziąć pod uwagę następujące zalecenia dotyczące uzyskania lepszej wydajności:  
  
- Jeśli aplikacja wymaga wyświetlania obrazów miniatur, należy rozważyć utworzenie zmniejszonej wersji obrazu. Domyślnie program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ładuje obraz i dekoduje go do pełnego rozmiaru. Jeśli potrzebujesz tylko miniatury obrazu, niepotrzebnie dekoduje obraz do jego pełnego rozmiaru, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a następnie skaluje go do rozmiaru miniatury. Aby uniknąć tego niepotrzebnego obciążenia, można albo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zażądać Dekodowanie obrazu do rozmiaru miniatury, albo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zażądać załadowania obrazu rozmiaru miniatury.  
  
- Zawsze Dekoduj obraz do żądanego rozmiaru, a nie do rozmiaru domyślnego. Jak wspomniano powyżej, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Poproś o Dekodowanie obrazu do żądanego rozmiaru, a nie domyślnego pełnego rozmiaru. Ograniczy to nie tylko zestaw roboczy aplikacji, ale również szybkość wykonywania.  
  
- Jeśli to możliwe, Połącz obrazy w jeden obraz, na przykład pasek kliszy składający się z wielu obrazów.  
  
- Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 W przypadku animowania skali dowolnej mapy bitowej domyślny algorytm próbkowania obrazu o wysokiej jakości może czasami zużywać wystarczające zasoby systemowe, aby spowodować spadek liczby klatek, co skutecznie powoduje, że animacje Stutter. Ustawiając <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> Właściwość <xref:System.Windows.Media.RenderOptions> obiektu ,możnautworzyćpłynnąanimacjępodczasskalowaniamapybitowej.<xref:System.Windows.Media.BitmapScalingMode.LowQuality> <xref:System.Windows.Media.BitmapScalingMode.LowQuality>Tryb informuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparat renderowania o przełączeniu z algorytmu zoptymalizowanego pod kątem jakości do algorytmu zoptymalizowanego pod kątem szybkości podczas przetwarzania obrazów.  
  
 Poniższy przykład pokazuje, <xref:System.Windows.Media.BitmapScalingMode> jak ustawić dla obiektu obrazu.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Domyślnie program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie przechowuje w pamięci podręcznej renderowanej <xref:System.Windows.Media.TileBrush> zawartości obiektów, <xref:System.Windows.Media.DrawingBrush> takich <xref:System.Windows.Media.VisualBrush>jak i. W scenariuszach statycznych, w których żadna zawartość ani użycie <xref:System.Windows.Media.TileBrush> nie są zmieniane, ma sens, ponieważ zachowuje pamięć wideo. Nie ma sensu, gdy <xref:System.Windows.Media.TileBrush> za pomocą zawartości statycznej jest używany w sposób niestatyczny — na przykład gdy statyczny <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> jest mapowany na powierzchnię obracającego się obiektu 3W. Domyślnym zachowaniem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest ponowne renderowanie całej zawartości <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> dla każdej ramki, nawet jeśli zawartość ulega zmianie.  
  
 Ustawiając <xref:System.Windows.Media.RenderOptions.CachingHint%2A> Właściwość <xref:System.Windows.Media.RenderOptions> obiektu ,możnazwiększyćwydajnośćprzyużyciubuforowanychwersjiobiektówpędzlazrozdziałami.<xref:System.Windows.Media.CachingHint.Cache>  
  
 Wartości właściwości <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> <xref:System.Windows.Media.TileBrush> i są względnymi wartościami rozmiaru, które określają, kiedy należy ponownie wygenerować obiekt z powodu zmian w skali. <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> Na przykład <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> ustawiając właściwość na 2,0, należy ponownie wygenerować pamięć podręczną <xref:System.Windows.Media.TileBrush> dla tylko wtedy, gdy jej rozmiar przekracza dwukrotnie rozmiar bieżącej pamięci podręcznej.  
  
 Poniższy przykład pokazuje, jak używać opcji wskazówki buforowania dla <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
- [Animacja — porady i wskazówki](../graphics-multimedia/animation-tips-and-tricks.md)
