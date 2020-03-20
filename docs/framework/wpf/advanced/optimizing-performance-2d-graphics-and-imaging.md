---
title: 'Optymalizacja wydajności: grafika 2D i obrazowanie'
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
ms.openlocfilehash: 03b2b64736407bf54c9bf957fe93d2d3d6e343f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186765"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optymalizacja wydajności: grafika 2D i obrazowanie
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia szeroką gamę funkcji grafiki 2D i obrazowania, które można zoptymalizować pod kątem wymagań aplikacji. Ten temat zawiera informacje na temat optymalizacji wydajności w tych obszarach.  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>Rysowanie i kształty  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia <xref:System.Windows.Media.Drawing> zarówno <xref:System.Windows.Shapes.Shape> obiekty do reprezentowania graficznej zawartości rysunku. Jednak <xref:System.Windows.Media.Drawing> obiekty są prostsze <xref:System.Windows.Shapes.Shape> konstrukcje niż obiekty i zapewniają lepszą wydajność charakterystyki.  
  
 A <xref:System.Windows.Shapes.Shape> umożliwia narysowanie kształtu graficznego na ekranie. Ponieważ pochodzą one z <xref:System.Windows.FrameworkElement> klasy, <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz paneli i większości formantów.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje kilka warstw dostępu do grafiki i usług renderowania. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewniają wiele przydatnych funkcji, takich jak układ i obsługa zdarzeń. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele gotowych do użycia obiektów kształtu. Wszystkie obiekty kształtu <xref:System.Windows.Shapes.Shape> dziedziczą z klasy. Dostępne obiekty <xref:System.Windows.Shapes.Ellipse>kształtu to <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, , i .  
  
 <xref:System.Windows.Media.Drawing>obiekty, z drugiej strony, nie pochodzą <xref:System.Windows.FrameworkElement> z klasy i zapewniają implementację o mniejszej wadze do renderowania kształtów, obrazów i tekstu.  
  
 Istnieją cztery typy <xref:System.Windows.Media.Drawing> obiektów:  
  
- <xref:System.Windows.Media.GeometryDrawing>Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing>Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Rysuje tekst.  
  
- <xref:System.Windows.Media.DrawingGroup>Rysuje inne rysunki. Grupa rysunków służy do łączenia innych rysunków w pojedynczy rysunek złożony.  
  
 Obiekt <xref:System.Windows.Media.GeometryDrawing> jest używany do renderowania zawartości geometrii. Klasa <xref:System.Windows.Media.Geometry> i konkretne klasy, które z niej <xref:System.Windows.Media.CombinedGeometry> <xref:System.Windows.Media.EllipseGeometry>wynikają, takie jak , i <xref:System.Windows.Media.PathGeometry>, zapewniają środki do renderowania grafiki 2D, a także zapewniają wsparcie testowania trafień i przycinania. Obiekty geometrii mogą służyć na przykład do definiowania obszaru formantu lub do definiowania regionu klipu, który ma być stosowany do obrazu. Obiekty geometrii mogą być prostymi regionami, takimi jak prostokąty i okręgi, lub złożonymi obszarami utworzonymi z dwóch lub więcej obiektów geometrii. Bardziej złożone regiony geometryczne można <xref:System.Windows.Media.PathSegment>tworzyć, łącząc obiekty <xref:System.Windows.Media.ArcSegment> <xref:System.Windows.Media.BezierSegment>pochodne, takie jak , i <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na powierzchni <xref:System.Windows.Media.Geometry> klasa i <xref:System.Windows.Shapes.Shape> klasa są bardzo podobne. Oba są używane w renderowaniu grafiki 2D i oba mają podobne klasy <xref:System.Windows.Media.EllipseGeometry> betonowe, które pochodzą od nich, na przykład, i <xref:System.Windows.Shapes.Ellipse>. Istnieją jednak istotne różnice między tymi dwoma zestawami klas. Po pierwsze, <xref:System.Windows.Media.Geometry> klasa nie ma niektórych <xref:System.Windows.Shapes.Shape> funkcji klasy, takich jak możliwość rysowania się. Aby narysować obiekt geometrii, do wykonania operacji rysowania musi być używana inna klasa, taka jak DrawingContext, Drawing lub Path (warto zauważyć, że ścieżka jest kształtem). Właściwości renderowania, takie jak wypełnienie, obrys i grubość obrysu, znajdują się w klasie, która rysuje obiekt geometrii, podczas gdy obiekt kształtu zawiera te właściwości. Jednym ze sposobów myślenia o tej różnicy jest to, że obiekt geometrii definiuje region, na przykład okrąg, podczas gdy obiekt kształtu definiuje region, definiuje sposób wypełniania i konspektowania tego regionu oraz uczestniczy w systemie układu.  
  
 Ponieważ <xref:System.Windows.Shapes.Shape> obiekty pochodzą <xref:System.Windows.FrameworkElement> z klasy, za ich pomocą można dodać znacznie więcej zużycia pamięci w aplikacji. Jeśli naprawdę nie potrzebujesz <xref:System.Windows.FrameworkElement> funkcji zawartości graficznej, rozważ użycie <xref:System.Windows.Media.Drawing> obiektów o lżejszej wadze.  
  
 Aby uzyskać <xref:System.Windows.Media.Drawing> więcej informacji na temat obiektów, zobacz [Omówienie obiektów rysunkowych](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>Obiekty StreamGeometry  
 Obiekt <xref:System.Windows.Media.StreamGeometry> jest lekką <xref:System.Windows.Media.PathGeometry> alternatywą dla tworzenia kształtów geometrycznych. Należy <xref:System.Windows.Media.StreamGeometry> użyć, gdy trzeba opisać złożoną geometrię. <xref:System.Windows.Media.StreamGeometry>jest zoptymalizowany pod <xref:System.Windows.Media.PathGeometry> kątem obsługi wielu obiektów i <xref:System.Windows.Media.PathGeometry> działa lepiej w porównaniu do korzystania z wielu pojedynczych obiektów.  
  
 W poniższym przykładzie użyto składni atrybutu <xref:System.Windows.Media.StreamGeometry> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]do utworzenia trójkątnego w pliku .  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Aby uzyskać <xref:System.Windows.Media.StreamGeometry> więcej informacji na temat obiektów, zobacz [Tworzenie kształtu za pomocą streamgeometry .](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>Rysunku Obiekty wizowe  
 Obiekt <xref:System.Windows.Media.DrawingVisual> jest klasą rysunku odciążony, która służy do renderowania kształtów, obrazów lub tekstu. Ta klasa jest uważana za lekką, ponieważ nie zapewnia obsługi układu lub zdarzeń, co zwiększa jej wydajność. Z tego powodu rysunki są idealne dla tła i obiektów clipart. Aby uzyskać więcej informacji, zobacz [Korzystanie z drawingvisual Objects](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>
## <a name="images"></a>Obrazy  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obrazowanie zapewnia znaczną poprawę w stosunku do możliwości przetwarzania obrazu w poprzednich wersjach systemu Windows. Funkcje obrazowania, takie jak wyświetlanie mapy bitowej lub używanie obrazu na wspólnej formancie, były obsługiwane głównie przez interfejs GDI interfejsu urządzenia graficznego systemu Microsoft Windows lub interfejs programowania aplikacji Microsoft Windows GDI+ (API). Te interfejsy API zapewniały podstawowe funkcje obrazowania, ale brakowało funkcji, takich jak obsługa rozszerzalności kodeka i obsługa obrazów o wysokiej wierności. Interfejs API w programie WPF Imaging został przeprojektowany, aby przezwyciężyć niedociągnięcia interfejsów GDI i GDI+ i udostępnić nowy zestaw interfejsu API do wyświetlania i używania obrazów w aplikacjach.  
  
 Korzystając z obrazów, należy wziąć pod uwagę następujące zalecenia dotyczące uzyskania lepszej wydajności:  
  
- Jeśli aplikacja wymaga wyświetlania obrazów miniatur, należy rozważyć utworzenie wersji obrazu o zmniejszonym rozmiarze. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ładuje obraz i dekoduje go do pełnego rozmiaru. Jeśli chcesz tylko miniaturową wersję [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obrazu, niepotrzebne dekoduje obraz do jego pełnego rozmiaru, a następnie skaluje go do rozmiaru miniatury. Aby uniknąć tego niepotrzebnego obciążenia, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można zażądać dekodowania obrazu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do rozmiaru miniatury lub poprosić o załadowanie obrazu o rozmiarze miniatury.  
  
- Zawsze dekoduj obraz do żądanego rozmiaru, a nie do rozmiaru domyślnego. Jak wspomniano powyżej, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prośba o dekodowanie obrazu do żądanego rozmiaru, a nie domyślny pełny rozmiar. Zmniejszysz nie tylko zestaw roboczy aplikacji, ale także szybkość wykonywania.  
  
- Jeśli to możliwe, połącz obrazy w jeden obraz, na przykład pasek filmowy składający się z wielu obrazów.  
  
- Aby uzyskać więcej informacji, zobacz [Omówienie obrazowania](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>Tryb skalowania mapy bitowej  
 Podczas animowania skali dowolnej mapy bitowej domyślny algorytm ponownego próbkowania obrazu wysokiej jakości może czasami zużywać wystarczające zasoby systemowe, aby spowodować obniżenie szybkości klatek, co skutecznie powoduje zacinanie się animacji. Ustawiając <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> właściwość <xref:System.Windows.Media.RenderOptions> obiektu <xref:System.Windows.Media.BitmapScalingMode.LowQuality> na można utworzyć płynniejszą animację podczas skalowania mapy bitowej. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>tryb informuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] silnik renderowania, aby przełączyć się z algorytmu zoptymalizowanego pod kątem jakości do algorytmu zoptymalizowanego pod kątem szybkości podczas przetwarzania obrazów.  
  
 W poniższym przykładzie <xref:System.Windows.Media.BitmapScalingMode> pokazano, jak ustawić dla obiektu obrazu.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint (CachingHint)  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie buforuje renderowanej <xref:System.Windows.Media.TileBrush> zawartości obiektów, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>takich jak i . W statycznych scenariuszach, <xref:System.Windows.Media.TileBrush> w których ani zawartość, ani użycie w scenie się zmienia, ma to sens, ponieważ oszczędza pamięć wideo. Nie ma to większego sensu, gdy zawartość statyczna <xref:System.Windows.Media.TileBrush> jest używana w sposób niestatyczny <xref:System.Windows.Media.DrawingBrush> — <xref:System.Windows.Media.VisualBrush> na przykład, gdy statyczny lub jest mapowany na powierzchni obracającego się obiektu 3D. Domyślnym zachowaniem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest ponowne renderowanie całej <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> zawartości lub dla każdej klatki, nawet jeśli zawartość jest niezmienna.  
  
 Ustawiając <xref:System.Windows.Media.RenderOptions.CachingHint%2A> właściwość <xref:System.Windows.Media.RenderOptions> obiektu <xref:System.Windows.Media.CachingHint.Cache> na można zwiększyć wydajność przy użyciu buforowanych wersji obiektów pędzla sąsiadująco.  
  
 Wartości <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> i właściwości są względnymi wartościami rozmiaru, które określają, kiedy <xref:System.Windows.Media.TileBrush> obiekt powinien zostać ponownie wygenerowany z powodu zmian w skali. Na przykład, ustawiając <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> właściwość na 2.0, pamięci podręcznej dla <xref:System.Windows.Media.TileBrush> tylko musi być ponowniegenerowany, gdy jego rozmiar przekracza dwukrotnie rozmiar bieżącej pamięci podręcznej.  
  
 W poniższym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingBrush>opcji podpowiedzi buforowania dla pliku .  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Zobacz też

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
