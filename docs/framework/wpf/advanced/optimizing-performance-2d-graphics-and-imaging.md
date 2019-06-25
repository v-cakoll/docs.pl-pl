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
ms.openlocfilehash: 25803bd772832cd22e855f530d10a3f3639c180c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348444"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optymalizacja wydajności: Grafika 2D i obrazowanie
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia szeroką gamę grafika 2D i funkcji przetwarzania obrazów, które mogą być optymalizowane dla wymagań aplikacji. Ten temat zawiera informacje dotyczące optymalizacji wydajności w tych obszarach.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Rysowanie i kształtów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia <xref:System.Windows.Media.Drawing> i <xref:System.Windows.Shapes.Shape> obiekty do reprezentowania graficzny zawartość rysowania. Jednak <xref:System.Windows.Media.Drawing> obiekty są konstrukcje prostsze niż <xref:System.Windows.Shapes.Shape> obiektów i zapewniają lepsze charakterystyki wydajności.  
  
 A <xref:System.Windows.Shapes.Shape> umożliwia rysowanie graficznego kształt na ekranie. Ponieważ są pochodną <xref:System.Windows.FrameworkElement> klasy <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz paneli i większość formantów.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje kilka warstw dostępu do grafiki i renderowania usług. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewnia wiele przydatnych funkcji, takich jak układ i obsługa zdarzeń. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje pewną liczbę obiektów kształtu gotowych do użycia. Wszystkie obiekty kształtów dziedziczyć <xref:System.Windows.Shapes.Shape> klasy. Kształt dostępne obiekty zawierają <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, i <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> obiekty, z drugiej strony, pochodzi z <xref:System.Windows.FrameworkElement> klasy i udostępnić implementację lekki renderowania kształtów, obrazy i tekst.  
  
 Istnieją cztery rodzaje <xref:System.Windows.Media.Drawing> obiektów:  
  
- <xref:System.Windows.Media.GeometryDrawing> Rysuje kształt.  
  
- <xref:System.Windows.Media.ImageDrawing> Rysuje obraz.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> Rysuje tekst.  
  
- <xref:System.Windows.Media.DrawingGroup> Rysuje inne rysunki. Aby połączyć inne rysunki w jeden złożony, należy użyć rysowania grupy.  
  
 <xref:System.Windows.Media.GeometryDrawing> Obiekt jest używany do renderowania zawartości geometrii. <xref:System.Windows.Media.Geometry> Klasy i konkretnych klas, które dziedziczyć po nim, takie jak <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, i <xref:System.Windows.Media.PathGeometry>, zapewniają środki do renderowania grafiki 2D, a także testowanie trafień i pomocy technicznej wycinka. Obiekty geometrii może służyć do definiowania z regionem danej kontrolki, na przykład, lub aby zdefiniować obszar przycinania do zastosowania do obrazu. Obiekty geometrii mogą być proste regionów, takie jak prostokąty i okręgów lub złożone regionów utworzone na podstawie dwóch lub więcej obiektów geometrii. Można utworzyć bardziej złożone regionów geometryczne, łącząc <xref:System.Windows.Media.PathSegment>-pochodnych obiektów, takich jak <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, i <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na powierzchni <xref:System.Windows.Media.Geometry> klasy i <xref:System.Windows.Shapes.Shape> klasy są bardzo podobne. Oba są używane w przypadku renderowania grafiki 2D i mają podobne konkretnych klas pochodzących od nich, na przykład <xref:System.Windows.Media.EllipseGeometry> i <xref:System.Windows.Shapes.Ellipse>. Istnieją istotne różnice między tymi dwoma zestawami klasy. Dla jednego <xref:System.Windows.Media.Geometry> klasa zamknięta nie ma niektórych funkcji <xref:System.Windows.Shapes.Shape> klasę, takie jak pobierające sam. Aby narysować obiekt geometry, innej klasy, takie jak DrawingContext, rysowania lub ścieżkę (warto zauważyć, że ścieżka jest kształt) musi służyć do wykonywania operacji rysowania. Renderowanie właściwości, takie jak wypełnienia, obrysu i grubość pociągnięć znajdują się na klasę, która pobiera obiekt geometry, a obiekt shape zawiera te właściwości. Jednym ze sposobów myślenia o różnica ta jest obiektu geometrii definiuje region, okrąg na przykład, gdy obiekt shape definiuje region, definiuje, jak ten region jest wypełniony i opisane i uczestniczy w system układu.  
  
 Ponieważ <xref:System.Windows.Shapes.Shape> obiektów pochodzić od <xref:System.Windows.FrameworkElement> klasy, ich użycie można dodać znacznie więcej zużycie pamięci w aplikacji. Jeśli tak naprawdę nie potrzebujesz <xref:System.Windows.FrameworkElement> funkcje graficzne zawartości, należy wziąć pod uwagę przy użyciu lekki <xref:System.Windows.Media.Drawing> obiektów.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Streamgeometry — obiekty  
 <xref:System.Windows.Media.StreamGeometry> Obiekt jest uproszczone zamiast <xref:System.Windows.Media.PathGeometry> do tworzenia kształtów geometrycznych. Użyj <xref:System.Windows.Media.StreamGeometry> niezbędne, aby opisać złożonych geometrii. <xref:System.Windows.Media.StreamGeometry> jest zoptymalizowany pod kątem obsługi wielu <xref:System.Windows.Media.PathGeometry> obiektów i działa lepiej w porównaniu z przy użyciu wielu osoba <xref:System.Windows.Media.PathGeometry> obiektów.  
  
 W poniższym przykładzie użyto składni atrybutów, aby utworzyć trójkątna <xref:System.Windows.Media.StreamGeometry> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.StreamGeometry> obiekty, zobacz [utworzyć kształt używając StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Obiekty DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Obiektu to lekkie rysowania klasę, która jest używany do renderowania kształty, obrazy i tekst. Ta klasa jest uważany za uproszczone, ponieważ nie dostarcza obsługi układu lub zdarzeń, która zwiększa ich wydajność. Z tego powodu rysunki są doskonałe do tła i obiekty clipart. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektów DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Obrazy  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Tworzenie obrazów zapewnia istotnej poprawy możliwości przetwarzania obrazów w poprzednich wersjach programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Tworzenie obrazu funkcji, takich jak wyświetlanie mapy bitowej lub za pomocą obrazu na formancie wspólnego przede wszystkim zostały obsłużone przez program Microsoft Windows GDI Graphics Device Interface () lub Microsoft Windows GDI + interfejsu programowania aplikacji (API). Tych interfejsów API udostępniane funkcje obsługi obrazów linii bazowej, ale bez funkcji, takich jak obsługę rozszerzalność kodera-dekodera oraz obraz o dużej wierności. Interfejs API do tworzenia obrazów w WPF ma został przeprojektowany w celu wyeliminowanie wad GDI i GDI + i podaj nowy zestaw interfejsu API, aby wyświetlić obrazy i używać ich w aplikacjach.  
  
 Korzystając z obrazów, należy wziąć pod uwagę następujące zalecenia zapewniające lepszą wydajność:  
  
- Jeśli aplikacja wymaga wyświetlić obrazy miniatur, należy rozważyć utworzenie zmniejszona o rozmiarze zerowym wersję obrazu. Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ładuje obraz i dekoduje go do pełnego rozmiaru. Jeśli chcesz tylko miniatury wersję obrazu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niepotrzebne dekoduje obrazu do jego pełnym rozmiarze i skaluje ją do rozmiaru miniatur. Aby uniknąć tego niepotrzebnych nakładów pracy, możesz zażądać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można dekodować obraz, który ma rozmiar miniatury lub zażądać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można załadować obrazu rozmiaru miniatur.  
  
- Zawsze dekodować obraz żądany rozmiar, a nie domyślny rozmiar. Jak wspomniano powyżej, żądanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do dekodowania obrazu żądany rozmiar i nie domyślne pełnym rozmiarze. Zmniejszy nie tylko aplikacji zestawu roboczego, ale również szybkości wykonywania.  
  
- Jeśli to możliwe połączyć obrazy w pojedynczy obraz, takie jak pasek filmu składa się z wielu obrazów.  
  
- Aby uzyskać więcej informacji, zobacz [Przegląd obrazowanie](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Gdy animowanie Skaluj wszelkie mapy bitowej, domyślny obraz o wysokiej jakości ponowne próbkowanie algorytm czasami mogą wykorzystywać wystarczających zasobów systemu, aby spowodować spadek współczynnik ramki, efektywnie powoduje animacji odtwarzanie przerywane. Ustawiając <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> właściwość <xref:System.Windows.Media.RenderOptions> obiekt <xref:System.Windows.Media.BitmapScalingMode.LowQuality> płynniejszą animację można utworzyć podczas skalowania mapy bitowej. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> Tryb informuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparat renderowania, aby przełączyć się z algorytmem zoptymalizowane pod kątem jakości jest algorytm zoptymalizowane pod kątem szybkości, podczas przetwarzania obrazów.  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Media.BitmapScalingMode> dla obiektu obrazu.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Domyślnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie będzie buforować zawartość renderowanych <xref:System.Windows.Media.TileBrush> obiekty, takie jak <xref:System.Windows.Media.DrawingBrush> i <xref:System.Windows.Media.VisualBrush>. W scenariuszach statyczne gdzie zawartości ani korzystania z <xref:System.Windows.Media.TileBrush> w scenie ulega zmianie, to sens, ponieważ zmniejsza jego wykorzystanie pamięci wideo. Nie powoduje ona jak znacznie sens, kiedy <xref:System.Windows.Media.TileBrush> z zawartości statycznej jest używane w taki sposób, niestatycznej — na przykład, kiedy statycznego <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> jest mapowany na powierzchni obiektu rotacji 3D. Domyślne zachowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest ponownego renderowania zawartości całego <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> w każdej klatce, nawet jeśli zawartość jest niezmiennych.  
  
 Ustawiając <xref:System.Windows.Media.RenderOptions.CachingHint%2A> właściwość <xref:System.Windows.Media.RenderOptions> obiekt <xref:System.Windows.Media.CachingHint.Cache> może zwiększyć wydajność przy użyciu pamięci podręcznej wersji obiektów fragmentacji pędzla.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> i <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> wartości właściwości są względne wartości, które określają, kiedy <xref:System.Windows.Media.TileBrush> obiekt powinien zostać ponownie wygenerowane z powodu zmian w skali. Na przykład, ustawiając <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> właściwości w wersji 2.0, pamięć podręczna <xref:System.Windows.Media.TileBrush> tylko musi być ponownie wygenerowany podczas jego rozmiar przekracza dwa razy większy od bieżącej pamięci podręcznej.  
  
 Poniższy przykład pokazuje, jak za pomocą opcji wskazówka buforowania <xref:System.Windows.Media.DrawingBrush>.  
  
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
