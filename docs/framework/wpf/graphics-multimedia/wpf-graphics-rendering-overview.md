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
ms.openlocfilehash: 09f5f026ed320aaa253d8cdf6e0b271235aff604
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004168"
---
# <a name="wpf-graphics-rendering-overview"></a>Przegląd Renderowanie grafiki WPF
Ten temat zawiera omówienie warstwy wizualizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Koncentruje się na roli klasy <xref:System.Windows.Media.Visual> do obsługi renderowania w modelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Rola obiektu wizualnego  
 Klasa <xref:System.Windows.Media.Visual> jest podstawowym abstrakcją, z której każdy obiekt <xref:System.Windows.FrameworkElement> dziedziczy. Służy również jako punkt wejścia do pisania nowych kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i na wiele sposobów można traktować jako uchwyt okna (HWND) w modelu aplikacji Win32.  
  
 Obiekt <xref:System.Windows.Media.Visual> jest podstawowym obiektem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], którego podstawową rolą jest zapewnienie obsługi renderowania. Kontrolki interfejsu użytkownika, takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.TextBox>, pochodzą z klasy <xref:System.Windows.Media.Visual> i używają jej do utrwalania danych renderowania. Obiekt <xref:System.Windows.Media.Visual> zapewnia obsługę dla:  
  
- Wyświetlanie danych wyjściowych: renderowanie utrwalonej i serializowanej zawartości rysunku wizualizacji.  
  
- Przekształcenia: wykonywanie transformacji na wizualizacji.  
  
- Przycinanie: zapewnianie obsługi regionu przycinania dla wizualizacji.  
  
- Testowanie trafień: Określanie, czy Współrzędna lub geometria znajduje się w granicach wizualizacji.  
  
- Obliczenia pola ograniczenia: Określanie prostokąta granicy wizualizacji.  
  
 Jednak obiekt <xref:System.Windows.Media.Visual> nie obejmuje obsługi funkcji niebędących renderowaniem, takich jak:  
  
- Obsługa zdarzeń  
  
- Układ  
  
- Style  
  
- Powiązanie danych  
  
- Globalizacja  
  
 <xref:System.Windows.Media.Visual> jest ujawniona jako publiczna klasa abstrakcyjna, z której muszą pochodzić klasy podrzędne. Na poniższej ilustracji przedstawiono hierarchię obiektów wizualnych, które są widoczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagram klas pochodnych dla obiektu wizualnego](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)    
  
### <a name="drawingvisual-class"></a>Klasa użycie DrawingVisual  
 @No__t-0 jest lekkim klasą rysowania, która jest używana do renderowania kształtów, obrazów lub tekstu. Ta klasa jest uznawana za uproszczoną, ponieważ nie zapewnia obsługi układu ani zdarzeń, co zwiększa wydajność środowiska uruchomieniowego. Z tego powodu rysunki są idealnym rozwiązaniem dla tła i clipartów. @No__t-0 może służyć do tworzenia niestandardowego obiektu wizualizacji. Aby uzyskać więcej informacji, zobacz [Korzystanie z obiektów użycie DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Klasa Viewport3DVisual  
 @No__t-0 udostępnia mostek między obiektami 2D <xref:System.Windows.Media.Visual> i <xref:System.Windows.Media.Media3D.Visual3D>. Klasa <xref:System.Windows.Media.Media3D.Visual3D> jest klasą bazową dla wszystkich elementów wizualnych 3W. @No__t-0 wymaga zdefiniowania wartości <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> i wartości <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A>. Aparat służy do wyświetlania sceny. Okienko ekranu określa miejsce, w którym Projekcja jest mapowana na powierzchnię 2D. Aby uzyskać więcej informacji na temat 3W w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Omówienie grafiki trójwymiarowej](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Klasa ContainerVisual  
 Klasa <xref:System.Windows.Media.ContainerVisual> jest używana jako kontener dla kolekcji obiektów <xref:System.Windows.Media.Visual>. Klasa <xref:System.Windows.Media.DrawingVisual> pochodzi od klasy <xref:System.Windows.Media.ContainerVisual>, co umożliwia jej zawieranie kolekcji obiektów wizualnych.  
  
### <a name="drawing-content-in-visual-objects"></a>Rysowanie zawartości w obiektach wizualnych  
 Obiekt <xref:System.Windows.Media.Visual> przechowuje dane renderowania jako **listę instrukcji grafiki wektorowej**. Każdy element na liście instrukcji reprezentuje zestaw danych graficznych i skojarzonych zasobów w serializowanym formacie. Istnieją cztery różne typy danych renderowania, które mogą zawierać zawartość rysunku.  
  
|Rysowanie typu zawartości|Opis|  
|--------------------------|-----------------|  
|Grafika wektorowa|Reprezentuje dane grafiki wektorowej i wszelkie skojarzone <xref:System.Windows.Media.Brush> i <xref:System.Windows.Media.Pen> informacji.|  
|Obraz|Reprezentuje obraz w regionie zdefiniowanym przez <xref:System.Windows.Rect>.|  
|Symbol|Reprezentuje rysunek, który renderuje <xref:System.Windows.Media.GlyphRun>, która jest sekwencją symboli z określonego zasobu czcionki. Jest to sposób reprezentowania tekstu.|  
|Plików|Reprezentuje rysunek, który renderuje wideo.|  
  
 @No__t-0 umożliwia wypełnienie <xref:System.Windows.Media.Visual> za pomocą zawartości wizualnej. W przypadku używania poleceń rysowania obiektu <xref:System.Windows.Media.DrawingContext> w rzeczywistości przechowujesz zestaw danych renderowania, które będą później używane przez system grafiki; nie rysujesz na ekranie w czasie rzeczywistym.  
  
 Podczas tworzenia formantu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takiego jak <xref:System.Windows.Controls.Button>, formant niejawnie generuje dane renderowania do rysowania. Na przykład ustawienie właściwości <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Button> powoduje, że kontrolka przechowa reprezentację glifu.  
  
 @No__t-0 opisuje swoją zawartość jako jeden lub więcej obiektów <xref:System.Windows.Media.Drawing> zawartych w <xref:System.Windows.Media.DrawingGroup>. @No__t-0 opisuje również maski nieprzezroczystości, przekształcenia, efekty bitmapowe i inne operacje, które są stosowane do jego zawartości. operacje <xref:System.Windows.Media.DrawingGroup> są stosowane w następującej kolejności, w której jest renderowana zawartość: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Poniższa ilustracja przedstawia kolejność, w jakiej podczas sekwencji renderowania są stosowane operacje <xref:System.Windows.Media.DrawingGroup>.  
  
 ![Kolejność wykonywania operacji](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji na obiektach do rysowania  
  
 Aby uzyskać więcej informacji, zobacz [Rysowanie obiektów — Omówienie](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Rysowanie zawartości w warstwie wizualnej  
 Nie można bezpośrednio utworzyć wystąpienia <xref:System.Windows.Media.DrawingContext>; można jednak uzyskać kontekst rysowania z określonych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Poniższy przykład pobiera <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> i używa go do rysowania prostokąta.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Wyliczanie zawartości rysowania w warstwie wizualnej  
 Oprócz innych celów, obiekty <xref:System.Windows.Media.Drawing> udostępniają również model obiektów do wyliczania zawartości <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
> Gdy wyliczasz zawartość wizualizacji, pobierasz <xref:System.Windows.Media.Drawing> obiektów, a nie źródłowa reprezentacja danych renderowania jako listy instrukcji grafiki wektorowej.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>, aby pobrać wartość <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Visual> i wyliczyć ją.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak obiekty wizualne są używane do kompilowania kontrolek  
 Wiele obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składa się z innych obiektów wizualnych, co oznacza, że mogą one zawierać różne hierarchie obiektów podrzędnych. Wiele elementów interfejsu użytkownika w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takich jak kontrolki, składa się z wielu obiektów wizualizacji reprezentujących różne typy elementów renderowania. Na przykład kontrolka <xref:System.Windows.Controls.Button> może zawierać wiele innych obiektów, w tym <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter> i <xref:System.Windows.Controls.TextBlock>.  
  
 Poniższy kod przedstawia kontrolkę <xref:System.Windows.Controls.Button> zdefiniowaną w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 W przypadku wyliczania obiektów wizualnych, które składają się na domyślną kontrolkę <xref:System.Windows.Controls.Button>, można znaleźć hierarchię obiektów wizualizacji przedstawionych poniżej:  
  
 ![Diagram hierarchii drzewa wizualnego](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif) 
  
 Kontrolka <xref:System.Windows.Controls.Button> zawiera element <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, który z kolei zawiera element <xref:System.Windows.Controls.ContentPresenter>. Element <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> jest odpowiedzialny za Rysowanie obramowania i tła dla <xref:System.Windows.Controls.Button>. Element <xref:System.Windows.Controls.ContentPresenter> jest odpowiedzialny za wyświetlanie zawartości <xref:System.Windows.Controls.Button>. W tym przypadku, ponieważ wyświetlasz tekst, element <xref:System.Windows.Controls.ContentPresenter> zawiera element <xref:System.Windows.Controls.TextBlock>. Fakt, że kontrola <xref:System.Windows.Controls.Button> używa <xref:System.Windows.Controls.ContentPresenter> oznacza, że zawartość może być reprezentowana przez inne elementy, takie jak <xref:System.Windows.Controls.Image> lub geometria, taka jak <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Szablony kontrolek  
 Kluczem do rozwinięcia kontrolki w hierarchii formantów jest <xref:System.Windows.Controls.ControlTemplate>. Szablon kontrolki określa domyślną hierarchię wizualną dla kontrolki. Gdy jawnie odwołujesz się do formantu, niejawnie odwołujesz się do jego hierarchii wizualnej. Można zastąpić domyślne wartości szablonu kontrolki, aby utworzyć dostosowany wygląd wizualizacji dla kontrolki. Na przykład można zmodyfikować wartość koloru tła kontrolki <xref:System.Windows.Controls.Button>, tak aby używała wartości koloru gradientu liniowego zamiast wartości pełnego koloru. Aby uzyskać więcej informacji, zobacz [Style i szablony przycisków](../controls/button-styles-and-templates.md).  
  
 Element interfejsu użytkownika, taki jak kontrolka <xref:System.Windows.Controls.Button>, zawiera kilka list instrukcji Vector Graphics, które opisują całą definicję renderowania kontrolki. Poniższy kod przedstawia kontrolkę <xref:System.Windows.Controls.Button> zdefiniowaną w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Jeśli chcesz wyliczyć obiekty wizualne i listy instrukcji grafiki wektorowej, które składają się na kontrolkę <xref:System.Windows.Controls.Button>, znajdziesz hierarchię obiektów przedstawionych poniżej:  
  
 ![Diagram drzewa wizualnego i dane renderowania](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Kontrolka <xref:System.Windows.Controls.Button> zawiera element <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, który z kolei zawiera element <xref:System.Windows.Controls.ContentPresenter>. Element <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> jest odpowiedzialny za rysowanie wszystkich odrębnych elementów graficznych, które tworzą obramowanie i tło przycisku. Element <xref:System.Windows.Controls.ContentPresenter> jest odpowiedzialny za wyświetlanie zawartości <xref:System.Windows.Controls.Button>. W tym przypadku, ponieważ wyświetlasz obraz, element <xref:System.Windows.Controls.ContentPresenter> zawiera element <xref:System.Windows.Controls.Image>.  
  
 Istnieje kilka punktów, które należy zwrócić uwagę na hierarchię obiektów wizualizacji i list instrukcji grafiki wektorowej:  
  
- Kolejność w hierarchii reprezentuje kolejność renderowania informacji o rysunku. Z głównego elementu wizualizacji elementy podrzędne są przenoszone, od lewej do prawej, od góry do dołu. Jeśli element ma wizualne elementy podrzędne, są one przenoszone przed elementami równorzędnymi elementu.  
  
- Elementy węzła spoza liścia w hierarchii, takie jak <xref:System.Windows.Controls.ContentPresenter>, są używane do przechowywania elementów podrzędnych — nie zawierają list instrukcji.  
  
- Jeśli element wizualizacji zawiera listę instrukcji grafiki wektorowej i wizualizację elementów podrzędnych, Lista instrukcji w elemencie nadrzędnym wizualizacji jest renderowana przed rysunki w dowolnym z obiektów podrzędnych wizualizacji.  
  
- Elementy na liście instrukcji grafiki wektorowej są renderowane od lewej do prawej.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Drzewo wizualne  
 Drzewo wizualne zawiera wszystkie elementy wizualne używane w interfejsie użytkownika aplikacji. Ponieważ element wizualizacji zawiera utrwalone informacje o rysunku, można traktować drzewo wizualne jako wykres sceny, zawierający wszystkie informacje dotyczące renderowania potrzebne do utworzenia danych wyjściowych na urządzeniu wyświetlającym. To drzewo jest akumulacją wszystkich elementów wizualizacji utworzonych bezpośrednio przez aplikację, niezależnie od tego, czy w kodzie czy w znacznikach. Drzewo wizualne zawiera również wszystkie elementy wizualne utworzone przez rozszerzenie szablonu elementów, takich jak kontrolki i obiekty danych.  
  
 Poniższy kod przedstawia element <xref:System.Windows.Controls.StackPanel> zdefiniowany w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 W przypadku wyliczania obiektów wizualnych wchodzących w skład <xref:System.Windows.Controls.StackPanel> w przykładzie znaczników można znaleźć hierarchię obiektów wizualizacji przedstawionych poniżej:  
  
 ![Diagram hierarchii drzewa wizualnego](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Kolejność renderowania  
 Drzewo wizualne określa kolejność renderowania dla wizualizacji i obiektów rysunkowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Kolejność przechodzenia rozpoczyna się od elementu głównego wizualizacji, który jest najwyższego poziomu w drzewie wizualnym. Elementy podrzędne wizualizacji głównej są następnie przenoszone, od lewej do prawej. Jeśli Wizualizacja ma elementy podrzędne, jego elementy podrzędne są przenoszone przed elementami równorzędnymi wizualizacji. Oznacza to, że zawartość wizualizacji podrzędnej jest renderowana przed treścią wizualizacji.  
  
 ![Diagram kolejności renderowania w drzewie wizualnym](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif) 
  
### <a name="root-visual"></a>Wizualizacja główna  
 **Główny element wizualny** jest najwyższego poziomu w hierarchii drzewa wizualnego. W większości aplikacji Klasa bazowa głównej wizualizacji ma wartość <xref:System.Windows.Window> lub <xref:System.Windows.Navigation.NavigationWindow>. Jednak w przypadku hostowania obiektów wizualnych w aplikacji Win32, główny element wizualny jest najwyższego poziomu wizualizacji, który był hostem w oknie Win32. Aby uzyskać więcej informacji, zobacz [Samouczek: hosting obiektów wizualnych w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relacja do drzewa logicznego  
 Drzewo logiczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentuje elementy aplikacji w czasie wykonywania. Chociaż nie manipulujesz tym drzewem bezpośrednio, ten widok aplikacji jest przydatny do interpretacji dziedziczenia właściwości i routingu zdarzeń. W przeciwieństwie do drzewa wizualnego, Drzewo logiczne może reprezentować obiekty danych niewizualnych, takie jak <xref:System.Windows.Documents.ListItem>. W wielu przypadkach Drzewo logiczne mapuje się bardzo blisko na definicje znaczników aplikacji. Poniższy kod przedstawia element <xref:System.Windows.Controls.DockPanel> zdefiniowany w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 W przypadku wyliczenia obiektów logicznych wchodzących w skład <xref:System.Windows.Controls.DockPanel> elementu w przykładzie znaczników można znaleźć hierarchię obiektów logicznych przedstawionych poniżej:  
  
 ![Diagram drzewa](./media/tree1-wcp.gif "Tree1_wcp")  
Diagram drzewa logicznego  
  
 Drzewo wizualne i Drzewo logiczne są synchronizowane z bieżącym zestawem elementów aplikacji, co odzwierciedla wszelkie Dodawanie, usuwanie lub modyfikowanie elementów. Jednak drzewa przedstawiają różne widoki aplikacji. W przeciwieństwie do drzewa wizualnego, Drzewo logiczne nie rozszerza elementu <xref:System.Windows.Controls.ContentPresenter> formantu. Oznacza to, że nie ma bezpośredniej relacji jeden-do-jednego między drzewem logicznym i drzewem wizualnym dla tego samego zestawu obiektów. W rzeczywistości wywoływanie metody <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> obiektu **LogicalTreeHelper** oraz metody <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> obiektu **VisualTreeHelper** przy użyciu tego samego elementu co parametr daje różne wyniki.  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Wyświetlanie drzewa wizualnego za pomocą Edytor XamlPad  
 Narzędzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Edytor XamlPad udostępnia opcję wyświetlania i eksplorowania drzewa wizualnego, które odpowiada aktualnie zdefiniowanej zawartości XAML. Kliknij przycisk **Pokaż drzewo wizualne** na pasku menu, aby wyświetlić drzewo wizualne. Poniżej ilustruje Rozszerzanie zawartości XAML do węzłów drzewa wizualnego w panelu programu **Visual Tree Explorer** Edytor XamlPad:  
  
 ![Panel Eksplorator drzewa wizualnego w Edytor XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Zwróć uwagę na to, jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Button> kontrolki wyświetlają osobną hierarchię obiektów wizualizacji w panelu programu **Visual Tree Explorer** Edytor XamlPad. Dzieje się tak, ponieważ kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają <xref:System.Windows.Controls.ControlTemplate>, które zawierają drzewo wizualne tej kontrolki. Gdy jawnie odwołujesz się do formantu, niejawnie odwołujesz się do jego hierarchii wizualnej.  
  
### <a name="profiling-visual-performance"></a>Profilowanie wydajności wizualizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera pakiet narzędzi profilowania wydajności, które umożliwiają analizowanie zachowania aplikacji w czasie wykonywania i Określanie typów optymalizacji wydajności, które można zastosować. Narzędzie Visual Profiler oferuje bogaty i graficzny widok danych wydajności przez mapowanie bezpośrednio do drzewa wizualnego aplikacji. Na tym zrzucie ekranu sekcja **użycie procesora** w programie Visual Profiler umożliwia precyzyjne rozbicie użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług, takich jak renderowanie i układ.  
  
 ![Program Visual Profiler wyświetla dane wyjściowe](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Wyświetlanie danych wyjściowych w programie Visual Profiler  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Zachowanie renderowania wizualnego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadza kilka funkcji, które wpływają na zachowanie renderowania obiektów wizualnych: grafika w trybie zachowanym, grafika wektorowa i niezależna od urządzenia grafika.  
  
### <a name="retained-mode-graphics"></a>Grafika w trybie zachowywania  
 Jednym z kluczy, aby zrozumieć rolę obiektu wizualnego, jest zrozumienie różnicy między **trybem bezpośrednim** i systemami graficznymi **trybu** przechowywania. Standardowa aplikacja Win32 oparta na interfejsie GDI lub GDI+ używa systemu grafiki trybu natychmiastowego. Oznacza to, że aplikacja jest odpowiedzialna za odświeżenie części obszaru klienta, która jest unieważniona, ze względu na działanie, takie jak rozmiar okna lub zmiana jego wyglądu.  
  
 ![Diagram sekwencji renderowania Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 W przeciwieństwie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa systemu trybu zachowywania. Oznacza to, że obiekty aplikacji, które mają wygląd wizualny, definiują zestaw serializowanych danych rysunku. Po zdefiniowaniu danych rysunku system będzie odpowiedzialny za odpowiadanie na wszystkie odświeże żądania renderowania obiektów aplikacji. Nawet w czasie wykonywania można modyfikować lub tworzyć obiekty aplikacji i nadal polegać na tym, że system odpowiada na żądania farb. Moc w systemie grafiki w trybie zachowanym polega na tym, że informacje o rysowaniu są zawsze utrwalane w stanie zserializowanym przez aplikację, ale pozostała odpowiedzialność w odróżnieniu od systemu. Na poniższym diagramie przedstawiono, w jaki sposób aplikacja korzysta z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w celu reagowania na żądania farb.  
  
 ![Diagram sekwencji renderowania WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Inteligentne rerysowanie  
 Jedną z największych korzyści wynikających z używania grafiki w trybie zachowywania jest to, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może efektywnie zoptymalizować, co należy wykonać w aplikacji. Nawet jeśli masz skomplikowaną scenę z różnymi poziomami nieprzezroczystości, zazwyczaj nie musisz pisać kodu specjalnego przeznaczenia, aby zoptymalizować ponowne Rysowanie. Porównaj to z programowaniem Win32, w którym można poświęcać dużo wysiłku na optymalizację aplikacji przez zminimalizowanie ilości rerysowania w regionie aktualizacji. Zobacz temat [rerysowanie w regionie aktualizacji](/windows/desktop/gdi/redrawing-in-the-update-region) , aby zapoznać się z przykładem typu złożoności związanej z optymalizacją rerysowania w aplikacjach Win32.  
  
### <a name="vector-graphics"></a>Grafika wektorowa  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa **grafiki wektorowej** jako formatu danych renderowania. Grafiki wektorowe, w tym skalowalne grafiki wektorowe (SVG), Windows metadanych (WMF) i TrueType — przechowują dane renderowania i przesyłają je jako listę instrukcji opisujących sposób ponownego tworzenia obrazu przy użyciu podstawowych elementów graficznych. Na przykład czcionki TrueType są czcionkami konturowymi opisującymi zestaw linii, krzywych i poleceń, a nie tablicą pikseli. Jedną z najważniejszych zalet grafiki wektorowej jest możliwość skalowania do dowolnego rozmiaru i rozdzielczości.  
  
 W przeciwieństwie do grafiki wektorowej Mapa bitowa grafiki przechowuje dane jako reprezentację pikseli w pikselach, które są wstępnie renderowane dla konkretnej rozdzielczości. Jedną z kluczowych różnic między formatami grafiki bitmapowej a wektorową jest wierność oryginalnego obrazu źródła. Na przykład gdy rozmiar obrazu źródłowego jest modyfikowany, bitmapowe systemy grafiki są rozciągane na obraz, natomiast systemy grafiki wektorowej skalują obraz, zachowując wierność obrazu.  
  
 Na poniższej ilustracji przedstawiono obraz źródłowy, którego rozmiar został zmieniony o 300%. Zauważ, że zniekształcenia pojawiają się, gdy obraz źródłowy zostanie rozciągnięty jako obraz grafiki mapy bitowej, a nie skalowany jako obraz grafiki wektorowej.  
  
 ![Różnice między grafiki rastrowej i wektorowej](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Poniższe znaczniki pokazują dwa elementy <xref:System.Windows.Shapes.Path> zdefiniowane. Drugi element używa <xref:System.Windows.Media.ScaleTransform>, aby zmienić rozmiar instrukcji rysowania pierwszego elementu o 300%. Zauważ, że instrukcje rysowania w elementach <xref:System.Windows.Shapes.Path> pozostaną niezmienione.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Informacje o rozdzielczości i grafiki niezależnej od urządzenia  
 Istnieją dwa czynniki systemowe, które określają rozmiar tekstu i grafiki na ekranie: rozdzielczość i DPI. Rozwiązanie opisuje liczbę pikseli, które pojawiają się na ekranie. Gdy rozdzielczość jest większa, piksele są mniejsze, co sprawia, że grafika i tekst będą mniejsze. Grafika wyświetlana na monitorze ustawionym na 1024 x 768 będzie wyglądać znacznie mniej, gdy rozdzielczość zostanie zmieniona na 1600 x 1200.  
  
 Inne ustawienie systemowe (DPI) określa rozmiar cala ekranu w pikselach. Większość systemów Windows ma wartość DPI 96, co oznacza, że cal wynosi 96 pikseli. Zwiększenie ustawienia DPI powoduje, że jest większym niż cal. zmniejszenie wartości DPI powoduje, że rozmiar ekranu jest mniejszy. Oznacza to, że rozmiar cala ekranu nie jest taki sam jak w przypadku rzeczywistego cala. w większości systemów prawdopodobnie nie jest to możliwe. W miarę zwiększania rozdzielczości DPI grafiki z obsługą rozdzielczości DPI i tekstu stają się większe, ponieważ zwiększono rozmiar cala ekranu. Zwiększenie rozdzielczości DPI może ułatwić odczytywanie tekstu, szczególnie w przypadku wysokiej rozdzielczości.  
  
 Nie wszystkie aplikacje są oparte na rozdzielczości DPI: niektóre z nich wykorzystują piksele sprzętowe jako podstawową jednostkę miary; Zmiana DPI systemu nie ma wpływu na te aplikacje. Wiele innych aplikacji używa jednostek z obsługą rozdzielczości DPI do opisywania rozmiarów czcionek, ale przy użyciu pikseli można opisać wszystko inne. Zbyt mała lub zbyt duża wartość DPI może spowodować problemy z układem dla tych aplikacji, ponieważ tekst aplikacji jest skalowany przy użyciu ustawienia DPI systemu, ale nie ma interfejsu użytkownika aplikacji. Ten problem został wyeliminowany dla aplikacji utworzonych przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje skalowanie automatyczne przy użyciu niezależnego piksela urządzenia jako podstawowej jednostki miary, a nie od pikseli sprzętu; Grafika i tekst są skalowane prawidłowo bez żadnej dodatkowej pracy z deweloperem aplikacji. Na poniższej ilustracji przedstawiono przykład, w jaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tekst i grafika są wyświetlane w różnych ustawieniach DPI.  
  
 ![Grafika i tekst w różnych ustawieniach dpi](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika i tekst w różnych ustawieniach DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>Klasa VisualTreeHelper  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> jest statyczną klasą pomocniczą, która udostępnia funkcje niskiego poziomu do programowania na poziomie obiektu wizualnego, co jest przydatne w przypadku bardzo konkretnych scenariuszy, takich jak tworzenie niestandardowych formantów o wysokiej wydajności. W większości przypadków obiekty platformy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wyższego poziomu, takie jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.TextBlock>, zapewniają większą elastyczność i łatwość użycia.  
  
### <a name="hit-testing"></a>Testowanie trafień  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> udostępnia metody testowania trafień w obiektach wizualnych, gdy domyślna obsługa testów trafień nie spełnia Twoich potrzeb. Można użyć metod <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> w klasie <xref:System.Windows.Media.VisualTreeHelper>, aby określić, czy wartość współrzędnej geometrii lub punktu znajduje się w granicach danego obiektu, takich jak kontrolka lub element graficzny. Na przykład możesz użyć testowania trafień, aby określić, czy kliknięcie myszą w obrębie prostokąta otaczającego obiektu znajduje się w obrębie geometrii okręgu, możesz również zastąpić domyślną implementację testu trafień, aby wykonać własny niestandardowy test trafień obliczeń.  
  
 Aby uzyskać więcej informacji na temat testowania trafień, zobacz [test trafień w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Wyliczanie drzewa wizualnego  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> oferuje funkcje wyliczania elementów członkowskich drzewa wizualnego. Aby pobrać element nadrzędny, wywołaj metodę <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A>. Aby pobrać element podrzędny lub bezpośrednie obiekty podrzędne obiektu wizualnego, wywołaj metodę <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A>. Ta metoda zwraca podrzędny <xref:System.Windows.Media.Visual> elementu nadrzędnego o określonym indeksie.  
  
 Poniższy przykład pokazuje, jak wyliczyć wszystkie elementy podrzędne obiektu wizualnego, który jest techniką, którą można chcieć użyć, jeśli interesują się wszystkie informacje renderowania hierarchii obiektów wizualnych.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 W większości przypadków Drzewo logiczne stanowi bardziej użyteczną reprezentację elementów w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Chociaż nie modyfikujesz bezpośrednio drzewa logicznego, ten widok aplikacji jest przydatny do znajomości dziedziczenia właściwości i routingu zdarzeń. W przeciwieństwie do drzewa wizualnego, Drzewo logiczne może reprezentować obiekty danych niewizualnych, takie jak <xref:System.Windows.Documents.ListItem>. Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](../advanced/trees-in-wpf.md).  
  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> zapewnia metody do zwrócenia prostokąta związanego z obiektami wizualnymi. Można zwrócić prostokąt ograniczenia obiektu wizualnego, wywołując <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Można zwrócić prostokąt ograniczenia wszystkich elementów podrzędnych obiektu wizualizacji, w tym sam obiekt wizualizacji, wywołując <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Poniższy kod pokazuje, jak obliczyć prostokąt związany z obiektem wizualnym i wszystkimi jego elementami podrzędnymi.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
- [Samouczek: hosting obiektów wizualnych w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optymalizacja wydajności aplikacji WPF](../advanced/optimizing-wpf-application-performance.md)
