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
ms.openlocfilehash: ea219d653e6f41f9ebeceb8f33803ebb9246d8bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962859"
---
# <a name="wpf-graphics-rendering-overview"></a>Przegląd Renderowanie grafiki WPF
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwy wizualnej. Koncentruje się na roli <xref:System.Windows.Media.Visual> klasy do obsługi renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w modelu.  

<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Rola obiektu wizualnego  
 Klasa stanowi podstawowe streszczenie, z którego pochodzi każdy <xref:System.Windows.FrameworkElement> obiekt. <xref:System.Windows.Media.Visual> Służy również jako punkt wejścia do pisania nowych kontrolek w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a na wiele sposobów można traktować jako uchwyt okna (HWND) w modelu aplikacji Win32.  
  
 Obiekt jest obiektem podstawowym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , którego podstawową rolą jest zapewnienie obsługi renderowania. <xref:System.Windows.Media.Visual> Kontrolki interfejsu użytkownika, takie <xref:System.Windows.Controls.Button> jak <xref:System.Windows.Controls.TextBox>i, pochodzą z <xref:System.Windows.Media.Visual> klasy i używają jej do utrwalania danych renderowania. <xref:System.Windows.Media.Visual> Obiekt zapewnia pomoc techniczną dla:  
  
- Wyświetlanie danych wyjściowych: Renderowanie utrwalonej i serializowanej zawartości rysunku wizualizacji.  
  
- Przekształcenia Wykonywanie transformacji na wizualizacji.  
  
- Wycinka Zapewnianie obsługi regionu przycinania dla wizualizacji.  
  
- Testowanie trafień: Określanie, czy Współrzędna lub geometria znajduje się w granicach wizualizacji.  
  
- Obliczenia pola ograniczenia: Określanie prostokąta ograniczenia wizualizacji.  
  
 <xref:System.Windows.Media.Visual> Jednak obiekt nie obejmuje obsługi funkcji niebędących renderowaniem, takich jak:  
  
- Obsługa zdarzeń  
  
- Układ  
  
- Style  
  
- Powiązanie danych  
  
- Globalizacja  
  
 <xref:System.Windows.Media.Visual>jest udostępniana jako publiczna klasa abstrakcyjna, z której muszą pochodzić klasy podrzędne. Na poniższej ilustracji przedstawiono hierarchię obiektów wizualnych, które są dostępne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie.  
  
 ![Diagram klas pochodnych dla obiektu wizualnego](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)    
  
### <a name="drawingvisual-class"></a>Klasa użycie DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Jest lekkim klasą rysowania, która jest używana do renderowania kształtów, obrazów lub tekstu. Ta klasa jest uznawana za uproszczoną, ponieważ nie zapewnia obsługi układu ani zdarzeń, co zwiększa wydajność środowiska uruchomieniowego. Z tego powodu rysunki są idealnym rozwiązaniem dla tła i clipartów. <xref:System.Windows.Media.DrawingVisual> Można go użyć do utworzenia niestandardowego obiektu wizualizacji. Aby uzyskać więcej informacji, zobacz [Korzystanie z obiektów użycie DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Klasa Viewport3DVisual  
 Zawiera mostek między 2D <xref:System.Windows.Media.Visual> i <xref:System.Windows.Media.Media3D.Visual3D> obiektów. <xref:System.Windows.Media.Media3D.Viewport3DVisual> <xref:System.Windows.Media.Media3D.Visual3D> Klasa jest klasą bazową dla wszystkich elementów wizualnych 3W. Wymaga zdefiniowania wartości i <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A>wartości. <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> <xref:System.Windows.Media.Media3D.Viewport3DVisual> Aparat służy do wyświetlania sceny. Okienko ekranu określa miejsce, w którym Projekcja jest mapowana na powierzchnię 2D. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3D w programie, zobacz temat [Omówienie grafiki trójwymiarowej](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Klasa ContainerVisual  
 Klasa jest używana jako kontener dla <xref:System.Windows.Media.Visual> kolekcji obiektów. <xref:System.Windows.Media.ContainerVisual> <xref:System.Windows.Media.DrawingVisual> Klasa dziedziczy<xref:System.Windows.Media.ContainerVisual> z klasy, umożliwiając jej zawiera kolekcję obiektów wizualnych.  
  
### <a name="drawing-content-in-visual-objects"></a>Rysowanie zawartości w obiektach wizualnych  
 Obiekt przechowuje dane renderowania jako **listę instrukcji grafiki wektorowej.** <xref:System.Windows.Media.Visual> Każdy element na liście instrukcji reprezentuje zestaw danych graficznych i skojarzonych zasobów w serializowanym formacie. Istnieją cztery różne typy danych renderowania, które mogą zawierać zawartość rysunku.  
  
|Rysowanie typu zawartości|Opis|  
|--------------------------|-----------------|  
|Grafika wektorowa|Reprezentuje dane grafiki wektorowej oraz wszelkie skojarzone <xref:System.Windows.Media.Brush> i <xref:System.Windows.Media.Pen> informacje.|  
|Obraz|Reprezentuje obraz w regionie zdefiniowanym przez <xref:System.Windows.Rect>.|  
|Symbol|Reprezentuje rysunek <xref:System.Windows.Media.GlyphRun>, który renderuje, który jest sekwencją symboli z określonego zasobu czcionki. Jest to sposób reprezentowania tekstu.|  
|Połączenia wideo|Reprezentuje rysunek, który renderuje wideo.|  
  
 <xref:System.Windows.Media.DrawingContext> Umożliwia<xref:System.Windows.Media.Visual> wypełnienie przy użyciu zawartości wizualnej. W przypadku korzystania z <xref:System.Windows.Media.DrawingContext> poleceń rysowania obiektu w rzeczywistości przechowujesz zestaw danych renderowania, które będą później używane przez system grafiki. nie rysujesz na ekranie w czasie rzeczywistym.  
  
 Podczas tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki, takiej <xref:System.Windows.Controls.Button>jak, formant niejawnie generuje dane renderowania do samego rysowania. Na przykład ustawienie <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości <xref:System.Windows.Controls.Button> powoduje, że kontrolka będzie przechowywać reprezentację glifu.  
  
 Opisuje jego zawartość jako co najmniej jeden <xref:System.Windows.Media.Drawing> obiekt zawarty w <xref:System.Windows.Media.DrawingGroup>. <xref:System.Windows.Media.Visual> Opisuje <xref:System.Windows.Media.DrawingGroup> również maski nieprzezroczystości, przekształcenia, efekty bitmapowe i inne operacje, które są stosowane do jego zawartości. <xref:System.Windows.Media.DrawingGroup>operacje są stosowane w następującej kolejności, gdy zawartość jest renderowana <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>: <xref:System.Windows.Media.DrawingGroup.Opacity%2A> <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>,,, i <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Na poniższej ilustracji przedstawiono kolejność, w jakiej <xref:System.Windows.Media.DrawingGroup> operacje są stosowane podczas sekwencji renderowania.  
  
 ![Kolejność operacji na rysunku](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji na obiektach do rysowania  
  
 Aby uzyskać więcej informacji, zobacz [Rysowanie obiektów — Omówienie](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Rysowanie zawartości w warstwie wizualnej  
 Nigdy nie tworzysz bezpośrednio wystąpienia <xref:System.Windows.Media.DrawingContext>. Możesz jednak uzyskać kontekst rysowania z określonych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Poniższy przykład pobiera <xref:System.Windows.Media.DrawingContext> a <xref:System.Windows.Media.DrawingVisual> z i używa go do rysowania prostokąta.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Wyliczanie zawartości rysowania w warstwie wizualnej  
 Oprócz innych obiektów, <xref:System.Windows.Media.Drawing> obiekty również udostępniają model obiektów do wyliczania zawartości. <xref:System.Windows.Media.Visual>  
  
> [!NOTE]
> Gdy wyliczasz zawartość wizualizacji, pobierasz <xref:System.Windows.Media.Drawing> obiekty, a nie źródłowa reprezentacja danych renderowania jako listę instrukcji grafiki wektorowej.  
  
 W poniższym przykładzie zastosowano <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, aby <xref:System.Windows.Media.DrawingGroup> pobrać wartość <xref:System.Windows.Media.Visual> a i wyliczyć ją.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak obiekty wizualne są używane do kompilowania kontrolek  
 Wiele obiektów w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składa się z innych obiektów wizualnych, co oznacza, że mogą one zawierać różne hierarchie obiektów podrzędnych. Wiele elementów interfejsu użytkownika w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takich jak kontrolki, składa się z wielu obiektów wizualizacji, reprezentujących różne typy elementów renderowania. Na przykład <xref:System.Windows.Controls.Button> kontrolka może zawierać wiele innych obiektów, takich jak <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, i <xref:System.Windows.Controls.TextBlock>.  
  
 Poniższy kod pokazuje <xref:System.Windows.Controls.Button> kontrolkę zdefiniowaną w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 W przypadku wyliczania obiektów wizualnych, które składają się na <xref:System.Windows.Controls.Button> formant domyślny, można znaleźć hierarchię obiektów wizualizacji przedstawionych poniżej:  
  
 ![Diagram hierarchii drzewa wizualnego](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif) 
  
 Kontrolka zawiera element, który <xref:System.Windows.Controls.ContentPresenter> z kolei zawiera element. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.Button> Element jest odpowiedzialny za Rysowanie obramowania i tła <xref:System.Windows.Controls.Button>dla. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element jest odpowiedzialny za wyświetlanie zawartości <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> W tym przypadku, ponieważ wyświetlasz tekst, <xref:System.Windows.Controls.ContentPresenter> element <xref:System.Windows.Controls.TextBlock> zawiera element. Fakt, że <xref:System.Windows.Controls.Button> formant <xref:System.Windows.Controls.ContentPresenter> używa metody oznacza, że zawartość może być reprezentowana przez inne <xref:System.Windows.Controls.Image> elementy, takie jak lub geometria, np <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Szablony kontrolek  
 Kluczem do rozwinięcia kontrolki w hierarchii formantów jest <xref:System.Windows.Controls.ControlTemplate>. Szablon kontrolki określa domyślną hierarchię wizualną dla kontrolki. Gdy jawnie odwołujesz się do formantu, niejawnie odwołujesz się do jego hierarchii wizualnej. Można zastąpić domyślne wartości szablonu kontrolki, aby utworzyć dostosowany wygląd wizualizacji dla kontrolki. Na przykład można zmodyfikować wartość <xref:System.Windows.Controls.Button> koloru tła kontrolki tak, aby używała wartości koloru gradientu liniowego zamiast wartości pełnego koloru. Aby uzyskać więcej informacji, zobacz [Style i szablony przycisków](../controls/button-styles-and-templates.md).  
  
 Element interfejsu użytkownika, taki jak <xref:System.Windows.Controls.Button> kontrolka, zawiera kilka list instrukcji grafiki wektorowej, które opisują całą definicję renderowania kontrolki. Poniższy kod pokazuje <xref:System.Windows.Controls.Button> kontrolkę zdefiniowaną w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 W przypadku wyliczenia obiektów wizualizacji i list instrukcji grafiki wektorowej, które składają się na <xref:System.Windows.Controls.Button> formant, można znaleźć hierarchię obiektów przedstawionych poniżej:  
  
 ![Diagram drzewa wizualnego i dane renderowania](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Kontrolka zawiera element, który <xref:System.Windows.Controls.ContentPresenter> z kolei zawiera element. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.Button> <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element jest odpowiedzialny za rysowanie wszystkich odrębnych elementów graficznych, które tworzą obramowanie i tło przycisku. Element jest odpowiedzialny za wyświetlanie zawartości <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> W tym przypadku, ponieważ wyświetlasz obraz, <xref:System.Windows.Controls.ContentPresenter> element <xref:System.Windows.Controls.Image> zawiera element.  
  
 Istnieje kilka punktów, które należy zwrócić uwagę na hierarchię obiektów wizualizacji i list instrukcji grafiki wektorowej:  
  
- Kolejność w hierarchii reprezentuje kolejność renderowania informacji o rysunku. Z głównego elementu wizualizacji elementy podrzędne są przenoszone, od lewej do prawej, od góry do dołu. Jeśli element ma wizualne elementy podrzędne, są one przenoszone przed elementami równorzędnymi elementu.  
  
- Elementy węzła spoza liścia w hierarchii, takie jak <xref:System.Windows.Controls.ContentPresenter>, są używane do przechowywania elementów podrzędnych — nie zawierają list instrukcji.  
  
- Jeśli element wizualizacji zawiera listę instrukcji grafiki wektorowej i wizualizację elementów podrzędnych, Lista instrukcji w elemencie nadrzędnym wizualizacji jest renderowana przed rysunki w dowolnym z obiektów podrzędnych wizualizacji.  
  
- Elementy na liście instrukcji grafiki wektorowej są renderowane od lewej do prawej.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Drzewo wizualne  
 Drzewo wizualne zawiera wszystkie elementy wizualne używane w interfejsie użytkownika aplikacji. Ponieważ element wizualizacji zawiera utrwalone informacje o rysunku, można traktować drzewo wizualne jako wykres sceny, zawierający wszystkie informacje dotyczące renderowania potrzebne do utworzenia danych wyjściowych na urządzeniu wyświetlającym. To drzewo jest akumulacją wszystkich elementów wizualizacji utworzonych bezpośrednio przez aplikację, niezależnie od tego, czy w kodzie czy w znacznikach. Drzewo wizualne zawiera również wszystkie elementy wizualne utworzone przez rozszerzenie szablonu elementów, takich jak kontrolki i obiekty danych.  
  
 Poniższy kod przedstawia <xref:System.Windows.Controls.StackPanel> element zdefiniowany w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Jeśli chcesz wyliczyć obiekty wizualizacji, które składają się <xref:System.Windows.Controls.StackPanel> na element w przykładzie znaczników, znajdziesz hierarchię obiektów wizualizacji przedstawionych poniżej:  
  
 ![Diagram hierarchii drzewa wizualnego](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Kolejność renderowania  
 Drzewo wizualne określa kolejność [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania obiektów wizualnych i rysunkowych. Kolejność przechodzenia rozpoczyna się od elementu głównego wizualizacji, który jest najwyższego poziomu w drzewie wizualnym. Elementy podrzędne wizualizacji głównej są następnie przenoszone, od lewej do prawej. Jeśli Wizualizacja ma elementy podrzędne, jego elementy podrzędne są przenoszone przed elementami równorzędnymi wizualizacji. Oznacza to, że zawartość wizualizacji podrzędnej jest renderowana przed treścią wizualizacji.  
  
 ![Diagram kolejności renderowania w drzewie wizualnym](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif) 
  
### <a name="root-visual"></a>Wizualizacja główna  
 **Główny** element wizualny jest najwyższego poziomu w hierarchii drzewa wizualnego. W większości aplikacji Klasa podstawowa wizualizacji głównej jest albo <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Jednak w przypadku hostowania obiektów wizualnych w aplikacji Win32, główny element wizualny jest najwyższego poziomu wizualizacji, który był hostem w oknie Win32. Aby uzyskać więcej informacji, [zobacz Samouczek: Hostowanie obiektów wizualnych w aplikacji](tutorial-hosting-visual-objects-in-a-win32-application.md)Win32.  
  
### <a name="relationship-to-the-logical-tree"></a>Relacja do drzewa logicznego  
 Drzewo logiczne w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentuje elementy aplikacji w czasie wykonywania. Chociaż nie manipulujesz tym drzewem bezpośrednio, ten widok aplikacji jest przydatny do interpretacji dziedziczenia właściwości i routingu zdarzeń. W przeciwieństwie do drzewa wizualnego, logiczne drzewo może reprezentować obiekty danych niewizualnych <xref:System.Windows.Documents.ListItem>, na przykład. W wielu przypadkach Drzewo logiczne mapuje się bardzo blisko na definicje znaczników aplikacji. Poniższy kod przedstawia <xref:System.Windows.Controls.DockPanel> element zdefiniowany w znaczniku.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 W przypadku wyliczenia obiektów logicznych wchodzących w skład <xref:System.Windows.Controls.DockPanel> elementu w przykładzie znaczników można znaleźć hierarchię obiektów logicznych przedstawionych poniżej:  
  
 ![Diagram drzewa](./media/tree1-wcp.gif "Tree1_wcp")  
Diagram drzewa logicznego  
  
 Drzewo wizualne i Drzewo logiczne są synchronizowane z bieżącym zestawem elementów aplikacji, co odzwierciedla wszelkie Dodawanie, usuwanie lub modyfikowanie elementów. Jednak drzewa przedstawiają różne widoki aplikacji. W przeciwieństwie do drzewa wizualnego, Drzewo logiczne nie rozszerza <xref:System.Windows.Controls.ContentPresenter> elementu kontrolki. Oznacza to, że nie ma bezpośredniej relacji jeden-do-jednego między drzewem logicznym i drzewem wizualnym dla tego samego zestawu obiektów. W rzeczywistości wywoływanie <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> metody obiektu **LogicalTreeHelper** i <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metody obiektu **VisualTreeHelper** przy użyciu tego samego elementu co parametr daje różne wyniki.  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Wyświetlanie drzewa wizualnego za pomocą Edytor XamlPad  
 Narzędzie, Edytor XamlPad, udostępnia opcję wyświetlania i eksplorowania drzewa wizualnego, które odpowiada aktualnie zdefiniowanej [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zawartości. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kliknij przycisk **Pokaż drzewo wizualne** na pasku menu, aby wyświetlić drzewo wizualne. Poniżej ilustruje rozszerzanie [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zawartości do węzłów drzewa wizualnego w panelu programu **Visual Tree Explorer** Edytor XamlPad:  
  
 ![Panel Eksplorator drzewa wizualnego w Edytor XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Zwróć uwagę na <xref:System.Windows.Controls.Label>to <xref:System.Windows.Controls.TextBox>, jak <xref:System.Windows.Controls.Button> , i kontroluje każdy wyświetla osobną hierarchię obiektów wizualnych w panelu **Eksplorator drzewa Visual** Edytor XamlPad. Wynika to z tego <xref:System.Windows.Controls.ControlTemplate> , że formantyzawierajądrzewowizualizacjitegoformantu.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Gdy jawnie odwołujesz się do formantu, niejawnie odwołujesz się do jego hierarchii wizualnej.  
  
### <a name="profiling-visual-performance"></a>Profilowanie wydajności wizualizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia pakiet narzędzi profilowania wydajności, które umożliwiają analizowanie zachowania aplikacji w czasie wykonywania i Określanie typów optymalizacji wydajności, które można zastosować. Narzędzie Visual Profiler oferuje bogaty i graficzny widok danych wydajności przez mapowanie bezpośrednio do drzewa wizualnego aplikacji. Na tym zrzucie ekranu sekcja **użycie procesora** w programie Visual Profiler zawiera precyzyjną strukturę użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług, takich jak renderowanie i układ.  
  
 ![Wyświetlanie danych wyjściowych w programie Visual Profiler](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Wyświetlanie danych wyjściowych w programie Visual Profiler  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Zachowanie renderowania wizualnego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wprowadza kilka funkcji, które wpływają na zachowanie renderowania obiektów wizualnych: grafika w trybie zachowanym, grafika wektorowa i niezależna od urządzenia grafika.  
  
### <a name="retained-mode-graphics"></a>Grafika w trybie zachowywania  
 Jednym z kluczy, aby zrozumieć rolę obiektu wizualnego, jest zrozumienie różnicy między **trybem bezpośrednim** i systemami graficznymi **trybu** przechowywania. Standardowa aplikacja Win32 oparta na interfejsie GDI lub GDI+ używa systemu grafiki trybu natychmiastowego. Oznacza to, że aplikacja jest odpowiedzialna za odświeżenie części obszaru klienta, która jest unieważniona, ze względu na działanie, takie jak rozmiar okna lub zmiana jego wyglądu.  
  
 ![Diagram sekwencji renderowania Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Z kolei program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa systemu trybu zachowywania. Oznacza to, że obiekty aplikacji, które mają wygląd wizualny, definiują zestaw serializowanych danych rysunku. Po zdefiniowaniu danych rysunku system będzie odpowiedzialny za odpowiadanie na wszystkie odświeże żądania renderowania obiektów aplikacji. Nawet w czasie wykonywania można modyfikować lub tworzyć obiekty aplikacji i nadal polegać na tym, że system odpowiada na żądania farb. Moc w systemie grafiki w trybie zachowanym polega na tym, że informacje o rysowaniu są zawsze utrwalane w stanie zserializowanym przez aplikację, ale pozostała odpowiedzialność w odróżnieniu od systemu. Na poniższym diagramie przedstawiono, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jaki sposób aplikacja korzysta z odpowiedzi na żądania farb.  
  
 ![Diagram sekwencji renderowania WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Inteligentne rerysowanie  
 Jedną z największych korzyści w korzystaniu z grafiki w trybie zachowanym jest to, że może efektywnie zoptymalizować, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] co należy ponownie narysować w aplikacji. Nawet jeśli masz skomplikowaną scenę z różnymi poziomami nieprzezroczystości, zazwyczaj nie musisz pisać kodu specjalnego przeznaczenia, aby zoptymalizować ponowne Rysowanie. Porównaj to z programowaniem Win32, w którym można poświęcać dużo wysiłku na optymalizację aplikacji przez zminimalizowanie ilości rerysowania w regionie aktualizacji. Zobacz temat [rerysowanie w regionie aktualizacji](/windows/desktop/gdi/redrawing-in-the-update-region) , aby zapoznać się z przykładem typu złożoności związanej z optymalizacją rerysowania w aplikacjach Win32.  
  
### <a name="vector-graphics"></a>Grafika wektorowa  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa **grafiki wektorowej** jako formatu danych renderowania. Grafiki wektorowe, w tym skalowalne grafiki wektorowe (SVG), Windows metadanych (WMF) i TrueType — przechowują dane renderowania i przesyłają je jako listę instrukcji opisujących sposób ponownego tworzenia obrazu przy użyciu podstawowych elementów graficznych. Na przykład czcionki TrueType są czcionkami konturowymi opisującymi zestaw linii, krzywych i poleceń, a nie tablicą pikseli. Jedną z najważniejszych zalet grafiki wektorowej jest możliwość skalowania do dowolnego rozmiaru i rozdzielczości.  
  
 W przeciwieństwie do grafiki wektorowej Mapa bitowa grafiki przechowuje dane jako reprezentację pikseli w pikselach, które są wstępnie renderowane dla konkretnej rozdzielczości. Jedną z kluczowych różnic między formatami grafiki bitmapowej a wektorową jest wierność oryginalnego obrazu źródła. Na przykład gdy rozmiar obrazu źródłowego jest modyfikowany, bitmapowe systemy grafiki są rozciągane na obraz, natomiast systemy grafiki wektorowej skalują obraz, zachowując wierność obrazu.  
  
 Na poniższej ilustracji przedstawiono obraz źródłowy, którego rozmiar został zmieniony o 300%. Zauważ, że zniekształcenia pojawiają się, gdy obraz źródłowy zostanie rozciągnięty jako obraz grafiki mapy bitowej, a nie skalowany jako obraz grafiki wektorowej.  
  
 ![Różnice między grafiki rastrowej i wektorowej](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Poniższe znaczniki pokazują dwa <xref:System.Windows.Shapes.Path> zdefiniowane elementy. Drugi element używa <xref:System.Windows.Media.ScaleTransform> do zmiany rozmiaru instrukcji rysowania pierwszego elementu o 300%. Zauważ, że instrukcje rysowania w <xref:System.Windows.Shapes.Path> elementach pozostaną niezmienione.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Informacje o rozdzielczości i grafiki niezależnej od urządzenia  
 Istnieją dwa czynniki systemowe, które określają rozmiar tekstu i grafiki na ekranie: rozdzielczość i DPI. Rozwiązanie opisuje liczbę pikseli, które pojawiają się na ekranie. Gdy rozdzielczość jest większa, piksele są mniejsze, co sprawia, że grafika i tekst będą mniejsze. Grafika wyświetlana na monitorze ustawionym na 1024 x 768 będzie wyglądać znacznie mniej, gdy rozdzielczość zostanie zmieniona na 1600 x 1200.  
  
 Inne ustawienie systemowe (DPI) określa rozmiar cala ekranu w pikselach. Większość systemów Windows ma wartość DPI 96, co oznacza, że cal wynosi 96 pikseli. Zwiększenie ustawienia DPI powoduje, że jest większym niż cal. zmniejszenie wartości DPI powoduje, że rozmiar ekranu jest mniejszy. Oznacza to, że rozmiar cala ekranu nie jest taki sam jak w przypadku rzeczywistego cala. w większości systemów prawdopodobnie nie jest to możliwe. W miarę zwiększania rozdzielczości DPI grafiki z obsługą rozdzielczości DPI i tekstu stają się większe, ponieważ zwiększono rozmiar cala ekranu. Zwiększenie rozdzielczości DPI może ułatwić odczytywanie tekstu, szczególnie w przypadku wysokiej rozdzielczości.  
  
 Nie wszystkie aplikacje są oparte na rozdzielczości DPI: niektóre z nich wykorzystują piksele sprzętowe jako podstawową jednostkę miary; Zmiana DPI systemu nie ma wpływu na te aplikacje. Wiele innych aplikacji używa jednostek z obsługą rozdzielczości DPI do opisywania rozmiarów czcionek, ale przy użyciu pikseli można opisać wszystko inne. Zbyt mała lub zbyt duża wartość DPI może spowodować problemy z układem dla tych aplikacji, ponieważ tekst aplikacji jest skalowany przy użyciu ustawienia DPI systemu, ale nie ma interfejsu użytkownika aplikacji. Ten problem został wyeliminowany w przypadku aplikacji utworzonych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przy użyciu programu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje automatyczne skalowanie przy użyciu niezależnego piksela urządzenia jako podstawowej jednostki miary, a nie od pikseli sprzętu; Grafika i tekst są skalowane prawidłowo bez żadnej dodatkowej pracy z deweloperem aplikacji. Na poniższej ilustracji przedstawiono przykład sposobu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wyświetlania tekstu i grafiki przy użyciu różnych ustawień DPI.  
  
 ![Grafika i tekst w różnych ustawieniach dpi](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika i tekst w różnych ustawieniach DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>Klasa VisualTreeHelper  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa jest statyczną klasą pomocniczą, która udostępnia funkcje niskiego poziomu do programowania na poziomie obiektu wizualnego, co jest przydatne w przypadku bardzo konkretnych scenariuszy, takich jak tworzenie niestandardowych formantów o wysokiej wydajności. W większości przypadków obiekty struktury wyższego poziomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , takie jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.TextBlock>, zapewniają większą elastyczność i łatwość użycia.  
  
### <a name="hit-testing"></a>Testowanie trafień  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa udostępnia metody testowania trafień w obiektach wizualnych, gdy domyślna obsługa testów trafień nie spełnia Twoich potrzeb. Możesz użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metod <xref:System.Windows.Media.VisualTreeHelper> w klasie, aby określić, czy wartość współrzędnej geometrii lub punktu znajduje się w granicach danego obiektu, takich jak kontrolka lub element graficzny. Na przykład możesz użyć testowania trafień, aby określić, czy kliknięcie myszą w obrębie prostokąta otaczającego obiektu znajduje się w obrębie geometrii okręgu, możesz również zastąpić domyślną implementację testu trafień, aby wykonać własny niestandardowy test trafień obliczeń.  
  
 Aby uzyskać więcej informacji na temat testowania trafień, zobacz [test trafień w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Wyliczanie drzewa wizualnego  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa zawiera funkcje do wyliczania elementów członkowskich drzewa wizualnego. Aby pobrać element nadrzędny, wywołaj <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metodę. Aby pobrać element podrzędny lub bezpośrednie obiekty podrzędne obiektu wizualnego, wywołaj <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metodę. Ta metoda zwraca element podrzędny <xref:System.Windows.Media.Visual> elementu nadrzędnego o określonym indeksie.  
  
 Poniższy przykład pokazuje, jak wyliczyć wszystkie elementy podrzędne obiektu wizualnego, który jest techniką, którą można chcieć użyć, jeśli interesują się wszystkie informacje renderowania hierarchii obiektów wizualnych.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 W większości przypadków Drzewo logiczne stanowi bardziej użyteczną reprezentację elementów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Chociaż nie modyfikujesz bezpośrednio drzewa logicznego, ten widok aplikacji jest przydatny do znajomości dziedziczenia właściwości i routingu zdarzeń. W przeciwieństwie do drzewa wizualnego, logiczne drzewo może reprezentować obiekty danych niewizualnych <xref:System.Windows.Documents.ListItem>, na przykład. Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](../advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa dostarcza metody do zwracania prostokąta związanego z obiektami wizualnymi. Można zwrócić prostokąt ograniczający obiekt wizualny przez wywołanie <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Można zwrócić prostokąt ograniczenia wszystkich elementów podrzędnych obiektu wizualizacji, w tym sam obiekt wizualizacji, wywołując <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Poniższy kod pokazuje, jak obliczyć prostokąt związany z obiektem wizualnym i wszystkimi jego elementami podrzędnymi.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
- [Samouczek: Hosting obiektów wizualnych w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optymalizacja wydajności aplikacji WPF](../advanced/optimizing-wpf-application-performance.md)
