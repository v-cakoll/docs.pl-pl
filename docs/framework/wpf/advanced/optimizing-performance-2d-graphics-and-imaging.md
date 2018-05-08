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
ms.openlocfilehash: 4e6b72dae863e89d70ec70c2cb99a5874581e9ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optymalizacja wydajności: grafika 2D i obrazowanie
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje szeroką gamę grafiki 2D oraz obsługi obrazów funkcje, które mogą być optymalizowane do wymagań aplikacji. Ten temat zawiera informacje o optymalizacji wydajności w tych obszarach.  
  
  
<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Rysowanie i kształtów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia zarówno <xref:System.Windows.Media.Drawing> i <xref:System.Windows.Shapes.Shape> obiekty do reprezentowania graficznego rysowania zawartości. Jednak <xref:System.Windows.Media.Drawing> obiekty są konstrukcje prostsze niż <xref:System.Windows.Shapes.Shape> obiekty i zapewnić lepszą charakterystyki wydajności.  
  
 A <xref:System.Windows.Shapes.Shape> umożliwia narysować kształt graficzny do ekranu. Ponieważ pochodzą z <xref:System.Windows.FrameworkElement> klasy <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz paneli i większość formantów.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje kilka warstw dostępu do usługi renderowania i grafiki. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i podaj wielu przydatnych funkcji, takich jak układ i obsługi zdarzeń. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera liczbę obiektów kształtu gotowe do użycia. Wszystkie obiekty kształtu dziedziczyć <xref:System.Windows.Shapes.Shape> klasy. Kształt dostępne obiekty obejmują <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, i <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> obiekty z drugiej strony, nie pochodzi od <xref:System.Windows.FrameworkElement> klasy i udostępnić implementację wagi jaśniejszego kształtów renderowania, obrazy i tekst.  
  
 Istnieją cztery typy <xref:System.Windows.Media.Drawing> obiektów:  
  
-   <xref:System.Windows.Media.GeometryDrawing> Rysuje kształt.  
  
-   <xref:System.Windows.Media.ImageDrawing> Rysuje obraz.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> Rysuje tekst.  
  
-   <xref:System.Windows.Media.DrawingGroup> Rysuje inne rysunki. Użyj grupy rysunku, aby połączyć inne rysunki w jeden złożonego.  
  
 <xref:System.Windows.Media.GeometryDrawing> Obiekt jest używany do renderowania zawartości geometrii. <xref:System.Windows.Media.Geometry> Konkretnych klas pochodzących od, takich jak i klasy <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, i <xref:System.Windows.Media.PathGeometry>, zapewniają środki do renderowania grafiki 2D, a także testowanie trafień i obsługa wycinka. Obiekty geometrii może służyć do definiowania region kontrolki, na przykład, lub aby zdefiniować obszar przycinania w celu zastosowania do obrazu. Geometria obiekty mogą być proste regionach, takie jak prostokąty i okręgi lub złożone regiony utworzone na podstawie co najmniej dwa obiekty geometrii. Można tworzyć bardziej złożone geometrycznych regionów łącząc <xref:System.Windows.Media.PathSegment>-pochodnych obiekty, takie jak <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, i <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na pierwszy rzut oka <xref:System.Windows.Media.Geometry> klasy i <xref:System.Windows.Shapes.Shape> klasy są bardzo podobne. Używany zarówno w przypadku renderowania grafiki 2D i mają podobne konkretnych klas pochodzących od nich, na przykład <xref:System.Windows.Media.EllipseGeometry> i <xref:System.Windows.Shapes.Ellipse>. Istnieją jednak istotne różnice między dwoma zestawami klas. Dla jednego <xref:System.Windows.Media.Geometry> klasy brakuje niektórych funkcji <xref:System.Windows.Shapes.Shape> klasy, takie jak pobierające samej siebie. Do rysowania obiektu geometrii, inną klasę, takich jak klasy DrawingContext, rysunku lub ścieżka (warto zauważyć, że ścieżka kształtu) może posłużyć do wykonania operacji rysowania. Renderowanie właściwości, takie jak wypełnienia, obrysu i grubość pociągnięć znajdują się na klasę, która pobiera obiektu geometrii, a obiekt shape zawiera te właściwości. Jednym ze sposobów traktować ta różnica jest obiektu geometrii definiuje obszar, okrąg na przykład podczas obiektu kształtu definiuje obszar, definiuje sposób wypełnione i opisane tego regionu i uczestniczy w systemie układu.  
  
 Ponieważ <xref:System.Windows.Shapes.Shape> obiektów pochodzi od <xref:System.Windows.FrameworkElement> klasa za ich pomocą można dodać znacznie więcej zużycie pamięci w aplikacji. Jeśli naprawdę nie trzeba <xref:System.Windows.FrameworkElement> funkcje graficzne zawartości, należy wziąć pod uwagę przy użyciu wagi jaśniejszego <xref:System.Windows.Media.Drawing> obiektów.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysunku](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Obiekty StreamGeometry  
 <xref:System.Windows.Media.StreamGeometry> Obiekt jest lekki zamiast <xref:System.Windows.Media.PathGeometry> tworzenia kształtów geometrycznych. Użyj <xref:System.Windows.Media.StreamGeometry> potrzebne do opisywania geometrii złożonych. <xref:System.Windows.Media.StreamGeometry> zoptymalizowana pod kątem obsługi wielu <xref:System.Windows.Media.PathGeometry> obiekty i działa lepiej w porównaniu z zastosowaniem wiele osób <xref:System.Windows.Media.PathGeometry> obiektów.  
  
 W poniższym przykładzie użyto Składnia atrybutu, aby utworzyć trójkątny <xref:System.Windows.Media.StreamGeometry> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.StreamGeometry> obiekty, zobacz [Utwórz kształt za pomocą StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Obiekty DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Obiektu to lekkie rysowania klasy, który jest używany do renderowania kształty, obrazy i tekst. Ta klasa jest traktowane jako lekkie, ponieważ nie dostarcza obsługi układu lub zdarzeń, co zwiększa wydajność. Z tego powodu rysunki idealnie nadają się do tła i grafik przycinania. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Obrazy  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Tworzenie obrazów udostępnia znaczne ulepszenia w porównaniu z możliwości przetwarzania obrazów w poprzednich wersjach [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Imaging możliwości, takie jak wyświetlanie mapy bitowej lub przy użyciu obrazu na formantu wspólnego głównie zostały obsłużone przez program Microsoft Windows graficzny interfejs urządzenia (GDI) lub interfejsu GDI + systemu Microsoft Windows interfejsu programowania aplikacji (API). Tych interfejsów API dostępny linii bazowej funkcje obsługi obrazów, ale brakuje funkcje, takie jak obsługa rozszerzalność kodera-dekodera i o wysokiej wierności obsługi obrazów. Interfejs API WPF Imaging przeprojektowano rozwiązać niedociągnięć GDI i GDI + i dostarczyć nowy zestaw interfejsu API do wyświetlanie i używanie obrazów w aplikacjach.  
  
 Przy użyciu obrazów, należy wziąć pod uwagę poniższe zalecenia do uzyskania lepszej wydajności:  
  
-   Jeśli aplikacja wymaga można wyświetlić obrazy miniatur, należy rozważyć utworzenie zmniejszenie wielkości wersję obrazu. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ładuje obraz i dekoduje go do pełnego rozmiaru. Jeśli chcesz tylko miniatur wersję obrazu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niepotrzebne dekoduje obrazu do jego pełnym rozmiarze i skaluje go do rozmiaru miniatur. Aby uniknąć tego niepotrzebne obciążenie, można albo żądania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do zdekodowania obrazu do rozmiaru miniatur, lub zwróć się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można załadować obrazu rozmiaru miniatur.  
  
-   Zawsze dekodować obrazu zgodnie z wymaganiami, a nie do domyślny rozmiar. Jak wspomniano powyżej, żądania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdekodować obrazu wymagany rozmiar i nie domyślne pełnego rozmiaru. Zmniejsza nie tylko aplikacji zestawu roboczego, ale również szybkości wykonywania.  
  
-   Jeśli to możliwe należy połączyć obrazów w pojedynczego obrazu, takie jak paska filmu składa się z wielu obrazów.  
  
-   Aby uzyskać więcej informacji, zobacz [Imaging omówienie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Gdy animacji skali wszystkie mapy bitowej, domyślny obraz wysokiej jakości ponownie próbkowania algorytm czasami mogą zużywać powodować spadku szybkość ramki, efektywnie powoduje animacji odtwarzanie przerywane wystarczających zasobów systemowych. Przez ustawienie <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> właściwość <xref:System.Windows.Media.RenderOptions> do obiektu <xref:System.Windows.Media.BitmapScalingMode.LowQuality> płynniejszą animację można tworzyć w czasie skalowania mapy bitowej. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> Określa tryb [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparatu renderowania, aby przełączyć się z algorytmem zoptymalizowanych pod względem jakości algorytmu zoptymalizowanych pod kątem szybkości, podczas przetwarzania obrazów.  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Media.BitmapScalingMode> dla obiekt obrazu.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie będzie buforować zawartość renderowanych <xref:System.Windows.Media.TileBrush> obiekty, takie jak <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>. W scenariuszach statycznych gdzie zawartości ani stosowania <xref:System.Windows.Media.TileBrush> w sceny jest zmieniany, to ma sens, ponieważ jego oszczędza pamięci wideo. Nie powoduje jako znacznie znaczeniu, kiedy <xref:System.Windows.Media.TileBrush> z zawartość statyczna jest używany w sposób niestatycznego — na przykład podczas statycznego <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> jest mapowany na powierzchni obiektu obracania 3D. Domyślne zachowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest ponownie renderowanie całą zawartość <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> dla każdej ramki, nawet jeśli zawartość jest niezmiennych.  
  
 Przez ustawienie <xref:System.Windows.Media.RenderOptions.CachingHint%2A> właściwość <xref:System.Windows.Media.RenderOptions> do obiektu <xref:System.Windows.Media.CachingHint.Cache> może zwiększyć wydajność przy użyciu pamięci podręcznej wersji obiektów sąsiadującym pędzla.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> i <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> wartości właściwości są wartości rozmiar względny, które określają podczas obliczania <xref:System.Windows.Media.TileBrush> obiekt powinien zostać wygenerowane ponownie z powodu zmian w skali. Na przykład przez ustawienie <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 2.0, w pamięci podręcznej dla właściwości <xref:System.Windows.Media.TileBrush> tylko musi być ponownie wygenerowany, gdy jego rozmiar przekracza dwa razy większy od bieżącej pamięci podręcznej.  
  
 Poniższy przykład przedstawia użycie opcji buforowania wskazówkę dla <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Animacja — porady i wskazówki](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
