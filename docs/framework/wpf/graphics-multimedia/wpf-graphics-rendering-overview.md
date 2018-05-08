---
title: Przegląd Renderowanie grafiki WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 305af1025abb98950d90f46e75a9f261704a8ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-graphics-rendering-overview"></a>Przegląd Renderowanie grafiki WPF
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual warstwy. Dotyczy on rolę <xref:System.Windows.Media.Visual> klasy renderowania pomocy technicznej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu.  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Rolę obiektu Visual  
 <xref:System.Windows.Media.Visual> Podstawowe abstrakcji, z którego jest klasa co <xref:System.Windows.FrameworkElement> pochodzi z obiektu. Służy również jako punkt wejścia dla zapisywania nowych formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i na wiele sposobów można traktować jako uchwyt okna (HWND) w modelu aplikacji Win32.  
  
 <xref:System.Windows.Media.Visual> Obiekt jest podstawowa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu, którego podstawową rolą jest zapewnia obsługę renderowania. Formanty interfejsu użytkownika, takich jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.TextBox>, pochodzi z <xref:System.Windows.Media.Visual> klasy, a następnie użyć jej do przechowywanie ich renderowania danych. <xref:System.Windows.Media.Visual> Obiektu zapewnia obsługę:  
  
-   Dane wyjściowe wyświetlania: renderowanie utrwalonego, serializacji rysowania zawartości obiektu visual.  
  
-   Przekształcenia: Przekształcenia element wizualny.  
  
-   Wycinka: Zapewnianie wycinka region obsługi dla obiektu visual.  
  
-   Testowanie trafień: Określanie, czy współrzędnych lub geometrii znajduje się w granicach obiektu visual.  
  
-   Ograniczenia pole obliczenia: Określanie prostokąt ograniczający element wizualny.  
  
 Jednak <xref:System.Windows.Media.Visual> obiektu nie obejmuje obsługę-rendering funkcji, takich jak:  
  
-   Obsługa zdarzeń  
  
-   Układ  
  
-   Style  
  
-   Powiązanie danych  
  
-   Globalizacja  
  
 <xref:System.Windows.Media.Visual> jest ujawniona jako publiczny klasa abstrakcyjna, z której klasy podrzędne muszą pochodzić. Na poniższej ilustracji przedstawiono hierarchii visual obiektów, które są widoczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagram klas pochodnych obiekt wizualny](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Hierarchia klas Visual  
  
### <a name="drawingvisual-class"></a>Klasa DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> To lekkie rysowania klasy, który jest używany do renderowania kształty, obrazy i tekst. Ta klasa jest traktowane jako lekkie, ponieważ nie dostarcza obsługi układu lub zdarzeń, co zwiększa wydajność środowiska uruchomieniowego. Z tego powodu rysunki idealnie nadają się do tła i grafik przycinania. <xref:System.Windows.Media.DrawingVisual> Może służyć do tworzenia niestandardowego obiektu visual. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Klasa Viewport3DVisual  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> Zapewnia mostka między 2D <xref:System.Windows.Media.Visual> i <xref:System.Windows.Media.Media3D.Visual3D> obiektów. <xref:System.Windows.Media.Media3D.Visual3D> Klasa jest klasą bazową dla wszystkich elementów wizualnych 3D. <xref:System.Windows.Media.Media3D.Viewport3DVisual> Wymaga zdefiniowania <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> wartość i <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> wartość. Aparat umożliwia wyświetlenie sceny. Okienko ekranu ustanawia, gdzie Rzutowanie na powierzchnię 2D. Aby uzyskać więcej informacji na temat 3D w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [3-Przegląd grafiki](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Klasa ContainerVisual  
 <xref:System.Windows.Media.ContainerVisual> Klasa jest używana jako kontener dla kolekcji <xref:System.Windows.Media.Visual> obiektów. <xref:System.Windows.Media.DrawingVisual> Pochodną klasy <xref:System.Windows.Media.ContainerVisual> klasy, dzięki któremu zawiera kolekcję obiektów visual.  
  
### <a name="drawing-content-in-visual-objects"></a>Rysowanie zawartości w obiektach Visual  
 A <xref:System.Windows.Media.Visual> obiekt przechowuje dane renderowania jako **listy instrukcji grafiki wektorowej**. Każdy element na liście instrukcji reprezentuje niskiego poziomu zestawu danych grafiki i skojarzonych zasobów format serializacji. Istnieją cztery różne typy danych renderowania, które mogą zawierać rysowania zawartości.  
  
|Typ zawartości do rysowania|Opis|  
|--------------------------|-----------------|  
|Grafika wektorowa|Reprezentuje wektorów danych grafiki i wszelkie powiązane <xref:System.Windows.Media.Brush> i <xref:System.Windows.Media.Pen> informacji.|  
|Obraz|Reprezentuje obraz w obrębie regionu zdefiniowane przez <xref:System.Windows.Rect>.|  
|Symbolu|Reprezentuje rysunku, który renderuje <xref:System.Windows.Media.GlyphRun>, czyli kolejność symboli z zasobu określonej czcionki. Jest to, jak tekstu jest wyświetlana.|  
|Video|Reprezentuje rysunku, który renderuje wideo.|  
  
 <xref:System.Windows.Media.DrawingContext> Służy do wypełniania <xref:System.Windows.Media.Visual> z zawartością visual. Jeśli używasz <xref:System.Windows.Media.DrawingContext> polecenia rysowania obiektu są faktycznie przechowywania zestaw danych renderowania, które będą później używane przez system grafiki; nie jest rysowany do ekranu w czasie rzeczywistym.  
  
 Po utworzeniu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolować, takich jak <xref:System.Windows.Controls.Button>, formant niejawnie generuje renderowania danych sam rysowania. Na przykład ustawienie <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button> powoduje, że formant do przechowywania renderowania reprezentację symbolu.  
  
 A <xref:System.Windows.Media.Visual> opisuje zawartość jako jeden lub więcej <xref:System.Windows.Media.Drawing> obiektów zawartych w <xref:System.Windows.Media.DrawingGroup>. A <xref:System.Windows.Media.DrawingGroup> opisano również nieprzezroczystość maski, transformacje efekty mapy bitowej i innych operacji, które są stosowane do jego zawartości. <xref:System.Windows.Media.DrawingGroup> operacje są stosowane w następującej kolejności podczas renderowania zawartości: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Na poniższej ilustracji przedstawiono kolejność, w którym <xref:System.Windows.Media.DrawingGroup> operacji są stosowane podczas renderowania sekwencji.  
  
 ![Kolejność operacji obiektu DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji DrawingGroup  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd obiektów rysunku](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Rysowanie zawartości w warstwie Visual  
 Użytkownik nigdy nie bezpośrednio utworzyć wystąpienia <xref:System.Windows.Media.DrawingContext>; można jednak uzyskać rysowania kontekstu z niektórych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Poniższy przykład pobiera <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> i używa go do rysowania prostokąta.  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Wyliczanie rysowania zawartości w warstwie Visual  
 Oprócz ich zastosowań <xref:System.Windows.Media.Drawing> obiekty także dostarczają model obiektowy wyliczania zawartość <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Gdy są wyliczania zawartość elementu wizualnego, są pobierane <xref:System.Windows.Media.Drawing> obiektów, a nie podstawowy reprezentację danych renderowania jako listę instrukcji grafiki wektorowej.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pobierania <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i jej wyliczyć.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak Visual obiekty służą do tworzenia kontrolek  
 Wiele obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składają się z innych obiektów visual, co oznacza mogą zawierać różne hierarchie obiekty zależne. Elementy w wielu użytkownika interfejsu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takich jak funkcje kontroli, składających się z wielu obiektów visual, reprezentująca różne rodzaje renderowania elementów. Na przykład <xref:System.Windows.Controls.Button> formant może zawierać wiele innych obiektów, w tym <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, i <xref:System.Windows.Controls.TextBlock>.  
  
 Poniższy kod przedstawia <xref:System.Windows.Controls.Button> kontroli zdefiniowane w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Zostałby wyliczyć obiektów visual, które składają się domyślnie <xref:System.Windows.Controls.Button> formantu, czy znaleźć hierarchię obiektów visual zostały pokazane poniżej:  
  
 ![Diagram hierarchii w drzewie wizualnym](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.gif "VisualLayerOverview03")  
Diagram hierarchii w drzewie wizualnym  
  
 <xref:System.Windows.Controls.Button> Formant zawiera <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, który z kolei zawiera <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element jest odpowiedzialny za rysowania obramowania i tło <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> Element odpowiada za wyświetlanie zawartości <xref:System.Windows.Controls.Button>. W takim przypadku ponieważ wyświetlanie tekstu, <xref:System.Windows.Controls.ContentPresenter> zawiera element <xref:System.Windows.Controls.TextBlock> elementu. Fakt który <xref:System.Windows.Controls.Button> kontrolować używa <xref:System.Windows.Controls.ContentPresenter> oznacza, że zawartość może być reprezentowany przez inne elementy, takie jak <xref:System.Windows.Controls.Image> lub geometry, takich jak <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Szablony formantu  
 Klucz do rozszerzenia kontrolki do hierarchii formantów jest <xref:System.Windows.Controls.ControlTemplate>. Szablon formantu określa domyślną hierarchię visual dla formantu. Jawnie odwołać formantu, można niejawnie odwołanie hierarchii visual. Można zastąpić wartości domyślne dla szablonu formantu do utworzenia dostosowanego wyglądu formantu. Na przykład można zmodyfikować wartości koloru tła <xref:System.Windows.Controls.Button> kontrolować, tak aby były używane zamiast wartości pełnego koloru wartość koloru gradientu liniowego. Aby uzyskać więcej informacji, zobacz [stylów przycisków i szablony](../../../../docs/framework/wpf/controls/button-styles-and-templates.md).  
  
 To interfejs użytkownika elementu, takich jak <xref:System.Windows.Controls.Button> kontrolować, zawiera kilka wektor grafiki instrukcji listy opisujące definicji całego renderowania formantu. Poniższy kod przedstawia <xref:System.Windows.Controls.Button> kontroli zdefiniowane w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Jeśli zostały do wyliczenia obiektów visual i wektorów list instrukcji grafiki, wchodzące w skład <xref:System.Windows.Controls.Button> formantu, czy znaleźć hierarchię obiektów, które zostały pokazane poniżej:  
  
 ![Diagram drzewa wizualnego i danych renderowania](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
Diagram drzewa wizualnego i renderowania danych  
  
 <xref:System.Windows.Controls.Button> Formant zawiera <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, który z kolei zawiera <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element jest odpowiedzialny za rysowania wszystkie odrębne elementy wchodzące w skład obramowania i tło przycisku. <xref:System.Windows.Controls.ContentPresenter> Element odpowiada za wyświetlanie zawartości <xref:System.Windows.Controls.Button>. W takim przypadku ponieważ wyświetlania obrazu <xref:System.Windows.Controls.ContentPresenter> zawiera element <xref:System.Windows.Controls.Image> elementu.  
  
 Istnieje wiele z uwagi na temat hierarchii obiektów visual i list instrukcji grafiki wektorowej:  
  
-   Określanie kolejności w hierarchii reprezentuje kolejność renderowania pobieranie informacji. Z głównego elementu wizualnego elementy podrzędne są przechodni, od lewej do prawej, od góry do dołu. Jeśli element ma elementy podrzędne visual, są one przechodni przed elementy równorzędne.  
  
-   Elementy innego niż liść węzeł w hierarchii, takie jak <xref:System.Windows.Controls.ContentPresenter>, są używane do przechowywania elementów podrzędnych — nie zawierają listy instrukcji.  
  
-   Jeśli element wizualny zawiera listę instrukcji grafiki wektorowej i elementów podrzędnych obiektów visual, instrukcji liście elementu nadrzędnego visual jest renderowany przed rysunki w jednym z obiektów podrzędnych visual.  
  
-   Elementy na liście instrukcji grafiki wektorowej są renderowane od lewej do prawej.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Drzewo wizualne  
 Drzewa wizualnego zawiera wszystkie elementy wizualne, używany w interfejsie użytkownika aplikacji. Ponieważ element wizualny zawiera utrwalonego pobieranie informacji, można traktować drzewa wizualnego jako wykres sceny zawierający wszystkie informacje renderowania, konieczne jest utworzenie danych wyjściowych do urządzenia. Tego drzewa jest sumą wszystkich elementów wizualnych tworzonych bezpośrednio przez aplikację, czy kod lub znaczników. Drzewa wizualnego zawiera również wszystkie elementy wizualne utworzone przez rozszerzenie szablonu elementów, takich jak kontrolek i obiekty danych.  
  
 Poniższy kod przedstawia <xref:System.Windows.Controls.StackPanel> elementu zdefiniowanego w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Zostałby wyliczyć obiektów visual wchodzące w skład <xref:System.Windows.Controls.StackPanel> element w przykładzie znaczników, może znaleźć hierarchii obiektów visual przedstawione poniżej:  
  
 ![Diagram hierarchii w drzewie wizualnym](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.gif "VisualLayerOverview05")  
Diagram hierarchii w drzewie wizualnym  
  
### <a name="rendering-order"></a>Kolejność renderowania  
 Drzewa wizualnego określa kolejność renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów visual i rysowania. Kolejność przechodzenie rozpoczyna się od katalogu głównego, wizualne, czyli najwyższy węzeł w drzewie wizualnym. Elementy podrzędne elementu wizualnego głównego jest następnie przesunięta, od lewej do prawej. Jeśli element wizualny ma elementy podrzędne, jego elementów podrzędnych jest przesunięta przed element wizualny na tym samym poziomie. Oznacza to, że zawartość elementu podrzędnego visual jest renderowany przed zawartości własnych visual.  
  
 ![Diagram drzewa wizualnego renderowania kolejności](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.gif "VisualLayerOverview06")  
Diagram drzewa wizualnego renderowania zlecenia  
  
### <a name="root-visual"></a>Główny Visual  
 **Główny visual** jest umieszczony najwyżej elementu w hierarchii w drzewie wizualnym. W większości aplikacji klasę podstawową klasy głównym visual jest <xref:System.Windows.Window> lub <xref:System.Windows.Navigation.NavigationWindow>. Jednak jeśli zostały hostingu visual obiektów w aplikacji Win32, główny visual się visual najwyższy, które zostały hosting w oknie Win32. Aby uzyskać więcej informacji, zobacz [samouczek: hostingu Visual obiektów w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relacja do drzewa logicznego  
 Drzewa logicznego w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentuje elementy aplikacji w czasie wykonywania. Chociaż tego drzewa nie manipulowania bezpośrednio, ten widok aplikacji jest przydatna do opis dziedziczenia właściwości i zdarzenia routingu. W przeciwieństwie do drzewa wizualnego drzewa logicznego może reprezentować Niewizualne danych obiektów, takich jak <xref:System.Windows.Documents.ListItem>. W wielu przypadkach drzewa logicznego mapuje bardzo ściśle definicji znaczników aplikacji. Poniższy kod przedstawia <xref:System.Windows.Controls.DockPanel> elementu zdefiniowanego w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Zostałby wyliczyć obiektów logiczne wchodzące w skład <xref:System.Windows.Controls.DockPanel> element w przykładzie znaczników, może znaleźć hierarchii obiektów logiczne zostały pokazane poniżej:  
  
 ![Diagram drzewa](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.gif "Tree1_wcp")  
Diagram drzewa logicznego  
  
 Drzewo wizualne i drzewa logicznego są synchronizowane z bieżącego zestawu elementów aplikacji odzwierciedlające żadnych dodawania, usuwania ani modyfikowania elementów. Jednak drzew przedstawia różne widoki aplikacji. W przeciwieństwie do drzewa wizualnego drzewa logicznego nie zwiększa formantu <xref:System.Windows.Controls.ContentPresenter> elementu. Oznacza to, że nie ma bezpośredniego odpowiednika między drzewa logicznego i drzewa wizualnego do tego samego zestawu obiektów. W rzeczywistości wywoływania **LogicalTreeHelper** obiektu <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> — metoda i **VisualTreeHelper** obiektu <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> przy użyciu tego samego elementu, ponieważ parametr daje różne wyniki — metoda .  
  
 Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Wyświetlanie drzewa wizualnego z edytor XamlPad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Narzędzie, edytor XamlPad, udostępnia opcję Wyświetlanie i przeglądanie drzewa wizualnego, który odpowiada do aktualnie zdefiniowanych [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zawartości. Kliknij przycisk **Pokaż drzewa wizualnego** przycisk paska menu, aby wyświetlić drzewa wizualnego. Poniżej przedstawiono rozszerzenia [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zawartości w węzłach drzewa wizualnego w **Visual drzewa Eksploratora** panelu edytor XamlPad:  
  
 ![Panel Eksploratora drzewa wizualnego w edytorze XamlPad](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
Panel Eksploratora drzewa wizualnego w edytorze XamlPad  
  
 Powiadomienie jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, i <xref:System.Windows.Controls.Button> formanty każdego wyświetlić hierarchię oddzielny obiekt visual w **Visual drzewa Eksploratora** panelu edytor XamlPad. Jest to spowodowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty mają <xref:System.Windows.Controls.ControlTemplate> zawierający drzewa wizualnego tego formantu. Jawnie odwołać formantu, można niejawnie odwołanie hierarchii visual.  
  
### <a name="profiling-visual-performance"></a>Profilowanie wydajności Visual  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia zestaw narzędzi, które umożliwiają analizowanie zachowania w czasie wykonywania aplikacji i określić typy optymalizacji wydajności, które można zastosować profilowania wydajności. Narzędzie profilera Visual udostępnia rozbudowane, graficznego widoku danych wydajności przez mapowanie bezpośrednio na drzewie wizualnym aplikacji. W tym zrzucie ekranu pokazano **użycie procesora CPU** sekcji profilera Visual umożliwia precyzyjne podział użycia obiektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług, takich jak renderowania i układu.  
  
 ![Wyświetla danych wyjściowych, profilera Visual](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Visual dane wyjściowe profilera  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Sposób renderowania Visual  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadzono kilka funkcji, które mają wpływ na sposób renderowania obiektów visual: zachowane tryb grafiki, grafiki wektorowej i grafiki niezależnie od urządzenia.  
  
### <a name="retained-mode-graphics"></a>Tryb zachowanych grafiki  
 Jeden z kluczy do zrozumienia rolę obiektu Visual jest zrozumieć różnicę między **trybie natychmiastowym** i **zachowane tryb** systemy graficzne. Standardowa aplikacją systemu Win32 na podstawie GDI lub GDI + używa systemu grafiki w trybie natychmiastowym. Oznacza to, że aplikacja jest odpowiedzialny za odświeżenie część obszaru klienta, który zostało unieważnione z powodu akcja, taka jak okno zmieniany, lub zmiana jego wygląd obiektu.  
  
 ![Diagram sekwencji renderowania Win32](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Diagram sekwencji renderowania Win32  
  
 Z kolei [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] korzysta z zachowanej tryb systemu. Oznacza to, że obiektów aplikacji, które mają wygląd zdefiniować zestaw danych rysowania serializacji. Po rysunku dane są zdefiniowane, system jest odpowiedzialny za następnie odpowiada na wszystkich żądań odświeżenia renderowania obiektów aplikacji. Nawet w czasie wykonywania można modyfikować lub tworzenie obiektów aplikacji i nadal korzystają z systemu odpowiada na żądania rysowania. Zasilania w systemie grafiki zachowanych tryb jest czy rysowanie informacji jest zawsze utrwalone w Zserializowany stan aplikacji, ale odpowiedzialność renderowania od lewej do systemu. Na poniższym diagramie przedstawiono, jak aplikacja korzysta z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiada namalować żądań.  
  
 ![Diagram sekwencji renderowania WPF](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
Diagram sekwencji renderowania WPF  
  
#### <a name="intelligent-redrawing"></a>Inteligentnego ponownego narysowania  
 Jedną z największych korzyści za pomocą zachowanych tryb grafiki jest to, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wydajnie zoptymalizować co musi zostać odświeżone w aplikacji. Nawet, jeśli masz złożonych sceny o różnej nieprzezroczystość zwykle nie trzeba napisać kod specjalnych zoptymalizować ponownego narysowania. To porównać programowania Win32, w którym trzeba poświęcić wiele wysiłku z optymalizacją zminimalizować ilość ponownego narysowania w regionie aktualizacji aplikacji. Zobacz [ponownego narysowania w regionie aktualizacji](https://msdn.microsoft.com/library/dd162909.aspx) na przykład typ złożoności zaangażowane w optymalizacji ponownego narysowania w aplikacjach systemu Win32.  
  
### <a name="vector-graphics"></a>Grafika wektorowa  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa **grafika wektorowa** jako formatem renderowania danych. Grafika wektorowa — które obejmują skalowalne wektor grafiki SVG metapliki Windows (WMF) i czcionki TrueType — przechowywanie danych renderowania i przekazuje je jako listę instrukcji zawierających opis sposobu ponownego tworzenia obrazu przy użyciu grafiki w nim elementów podstawowych. Na przykład czcionki TrueType są konspektu czcionek, które opisują zestaw linii, krzywych i poleceń, a nie tablicę pikseli. Jednym z kluczowych zalet grafika wektorowa jest możliwość skalowania do rozmiaru i rozpoznawania.  
  
 W przeciwieństwie do grafiki wektorowej grafiki mapy bitowej przechowywania danych renderowania jako reprezentacji poszczególne piksele obrazu wstępnie renderowana dla określonego rozwiązania. Jednym z podstawowych różnic między formaty graficzne mapy bitowej i wektor jest wierności do oryginalnego obrazu źródłowego. Na przykład podczas modyfikowania rozmiaru obrazu źródłowego systemy graficzne mapy bitowej obraz jest rozciągany tak, natomiast systemów grafiki wektorowej, skaluje obraz zachowuje wierności obrazu.  
  
 Na poniższej ilustracji przedstawiono obraz źródłowy, który został zmieniony przez 300%. Zwróć uwagę, zakłócenia, które są wyświetlane, gdy obraz źródłowy jest rozciągana jako obraz mapy bitowej grafiki, zamiast skalować jako obraz grafiki wektorowej.  
  
 ![Różnice między grafiki wektorowej i rastrowe](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
Różnice między grafiki wektorowej i rastrowe  
  
 Następujący kod przedstawia dwa <xref:System.Windows.Shapes.Path> elementy zdefiniowane. Drugi element używa <xref:System.Windows.Media.ScaleTransform> Aby zmienić rozmiar rysunku instrukcje pierwszego elementu 300%. Należy zauważyć, że instrukcje rysowania <xref:System.Windows.Shapes.Path> elementy pozostają niezmienione.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Informacje o rozdzielczości i grafice niezależnych od urządzenia  
 Istnieją dwa czynniki systemu, które określają rozmiaru tekstu i grafiki na ekranie: rozdzielczość i DPI. Rozdzielczość określa liczbę pikseli, które są wyświetlane na ekranie. Jak wyższa rozdzielczość jeszcze mniejsze, powodując grafiki i tekst są mniejsze. Grafiki wyświetlane na monitorze ustawioną 1024 x 768 będą wyświetlane znacznie mniejszy, gdy rozwiązanie jest zmieniana na 1600 x 1200 pikseli.  
  
 Inne ustawienia systemowego DPI, w tym artykule opisano rozmiar CAL ekranu w pikselach. Większość [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemy mają rozdzielczości 96, co oznacza CAL ekranu jest 96 pikseli. Zwiększyć ustawienie DPI sprawia, że CAL ekranu większą; zmniejszenie wartości DPI powoduje, że CAL ekranu mniejsze. Oznacza to, że CAL ekranu nie jest taki sam rozmiar jak cal rzeczywistych; w większości systemów, prawdopodobnie nie jest. Wraz ze zwiększaniem wartości DPI obsługującą ustawienia DPI grafiki i tekstu stać się większy ponieważ między innymi zwiększenie rozmiaru CAL ekranu. Zwiększenie wartości DPI może ułatwić tekstu do odczytania, szczególnie w wysokiej rozdzielczości.  
  
 Nie wszystkie aplikacje są obsługującą ustawienia DPI: niektóre użycie pikseli sprzętu jako podstawową jednostkę miary; Zmiana rozdzielczości DPI systemu nie ma wpływu na te aplikacje. Wiele innych aplikacji za pomocą jednostek obsługującą ustawienia DPI opisano rozmiary czcionek, ale do opisania wszystkich pozostałych używać pikseli. Wprowadzenie wartości DPI zbyt małej lub zbyt duży może spowodować problemy związane z układem w przypadku tych aplikacji, ponieważ tekst aplikacji skaluje ustawienie DPI systemu, ale nie ma interfejsu użytkownika aplikacji. Ten problem został wyeliminowany dla aplikacji utworzony przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje automatyczne skalowanie za pomocą pixel niezależnie od urządzenia jako jego podstawowy jednostkę, zamiast sprzętu pikseli; Grafika i tekst skalowana bez konieczności wykonywania dodatkowych działań z deweloperem aplikacji. Na poniższej ilustracji przedstawiono przykładowy sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tekstu i grafiki są wyświetlane różne ustawienia DPI.  
  
 ![Grafika i tekst w różne ustawienia DPI](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika i tekst w różne ustawienia DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>Klasa VisualTreeHelper  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa jest statyczną klasę pomocy którego niskiego poziomu funkcje programowania na poziomie visual obiektu, który jest przydatny w bardzo konkretnych scenariuszy, takich jak tworzenie niestandardowych formantów wysokiej wydajności. W większości przypadków wyższego poziomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework obiekty, takie jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.TextBlock>, zapewniają większą elastyczność i łatwość użycia.  
  
### <a name="hit-testing"></a>Testy trafienia  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa dostarcza metody do trafień testowania obiektów visual po naciśnięciu domyślna obsługa testu odpowiada Twoim potrzebom. Można użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod w <xref:System.Windows.Media.VisualTreeHelper> klasę, aby określić, czy wartość współrzędnych geometrii lub punkt znajduje się w granicy danego obiektu, takich jak kontrola lub elementu graficznego. Na przykład umożliwiają testowanie trafień ustalić, czy kliknięcie myszki w prostokątem obiektu mieści się w geometrii kółka, które można również zastąpić domyślną implementację testowania trafień przeprowadzić własne niestandardowe testu trafienia obliczenia.  
  
 Aby uzyskać więcej informacji na temat testowania trafień, zobacz [trafień testowania w warstwie Visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Wyliczanie drzewa wizualnego  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa udostępnia funkcje wyliczania elementów członkowskich drzewa wizualnego. Aby uzyskać dostęp do elementu nadrzędnego, należy wywołać <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metody. Aby pobrać obiekt podrzędny lub bezpośredniego podrzędny obiekt visual wywołać <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metody. Ta metoda zwraca element podrzędny <xref:System.Windows.Media.Visual> elementu nadrzędnego w określonym indeksie.  
  
 Poniższy przykład pokazuje, jak wyliczyć wszystkich elementów podrzędnych obiektu visual to technika, które możesz chcieć użyć gdyby zainteresowana serializacji wszystkie informacje renderowania hierarchii obiektu visual.  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 W większości przypadków drzewa logicznego jest bardziej praktyczne odwzorowanie elementów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Mimo że nie należy modyfikować drzewa logicznego bezpośrednio, tego widoku aplikacji jest przydatne w przypadku dziedziczenia właściwości i zdarzenia routingu. W przeciwieństwie do drzewa wizualnego drzewa logicznego może reprezentować Niewizualne danych obiektów, takich jak <xref:System.Windows.Documents.ListItem>. Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa dostarcza metody do zwracania prostokątem obiektów visual. Prostokąt ograniczający obiekt wizualny można zwrócić przez wywołanie metody <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Może zwrócić prostokątem wszystkich elementów podrzędnych obiektu visual, w tym obiekt visual, wywołując <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Poniższy kod przedstawia, jak można obliczyć prostokątem visual obiektu i wszystkich jego elementów podrzędnych.  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 <xref:System.Windows.Media.DrawingVisual>  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Test trafienia w warstwie wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Użycie obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [Samouczek: hosting obiektów wizualnych w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
