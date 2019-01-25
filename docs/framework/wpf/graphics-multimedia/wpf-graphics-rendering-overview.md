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
ms.openlocfilehash: 6323d27158855e5ded1698401835b35632bedebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603849"
---
# <a name="wpf-graphics-rendering-overview"></a>Przegląd Renderowanie grafiki WPF
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwy visual. Dotyczy on rolę <xref:System.Windows.Media.Visual> klasy renderowania pomocy technicznej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu.  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>Rola obiekt wizualny  
 <xref:System.Windows.Media.Visual> Klasa jest podstawowe abstrakcji, z których każdy <xref:System.Windows.FrameworkElement> pochodzi z obiektu. Służy również jako punkt wejścia dla zapisywania nowych kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a na wiele sposobów można traktować jako uchwyt okna (HWND) w modelu aplikacji Win32.  
  
 <xref:System.Windows.Media.Visual> Obiekt jest podstawowa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektu, którego podstawową rolą jest zapewnia obsługę renderowania. Kontrolki interfejsu użytkownika, takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.TextBox>, pochodzi od <xref:System.Windows.Media.Visual> klasy, a następnie użyć jej do utrwalania danych ich renderowania. <xref:System.Windows.Media.Visual> Obiektu zapewnia obsługę:  
  
-   Wyświetlanie danych wyjściowych: Renderowanie utrwalonych serializacji zawartość rysowania visual.  
  
-   Przekształcenia: Wykonywanie przekształceń na wizualizacji.  
  
-   Wycinek: Wspieranie wycinka region dla wizualizacji.  
  
-   Test trafienia: Określanie, czy współrzędne lub geometrii znajduje się w granicach wizualizacji.  
  
-   Otaczający obliczenia pola: Określanie prostokąt otaczający wizualizacji.  
  
 Jednak <xref:System.Windows.Media.Visual> obiektu nie obejmują obsługę-rendering funkcji, takich jak:  
  
-   Obsługa zdarzeń  
  
-   Układ  
  
-   Style  
  
-   Powiązanie danych  
  
-   Globalizacja  
  
 <xref:System.Windows.Media.Visual> jest udostępniany jako publiczny klasa abstrakcyjna, z których mogą pochodzić klasy podrzędne. Poniższa ilustracja pokazuje hierarchię obiektów wizualnych, które są widoczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagram klas pochodnych obiekt wizualny](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Hierarchia klas Visual  
  
### <a name="drawingvisual-class"></a>Klasa DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> To lekkie rysowania klasę, która jest używany do renderowania kształty, obrazy i tekst. Ta klasa jest uważany za uproszczone, ponieważ nie dostarcza obsługi układu lub zdarzeń, która zwiększa wydajność środowiska uruchomieniowego. Z tego powodu rysunki są doskonałe do tła i obiekty clipart. <xref:System.Windows.Media.DrawingVisual> Może służyć do tworzenia niestandardowych obiektów wizualnych. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Klasa Viewport3DVisual  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> Zapewnia mostek między 2D <xref:System.Windows.Media.Visual> i <xref:System.Windows.Media.Media3D.Visual3D> obiektów. <xref:System.Windows.Media.Media3D.Visual3D> Klasa jest klasą bazową dla wszystkich elementów wizualnych 3D. <xref:System.Windows.Media.Media3D.Viewport3DVisual> Wymaga zdefiniowania <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> wartość i <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> wartość. Aparat fotograficzny umożliwia wyświetlenie sceny. Okienko ekranu ustanawia, gdzie Rzutowanie na powierzchnię 2D. Aby uzyskać więcej informacji na temat 3D w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Przegląd grafiki 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Klasa ContainerVisual  
 <xref:System.Windows.Media.ContainerVisual> Klasa jest używana jako kontener dla kolekcji <xref:System.Windows.Media.Visual> obiektów. <xref:System.Windows.Media.DrawingVisual> Klasa pochodzi od <xref:System.Windows.Media.ContainerVisual> klasy, dzięki któremu zawiera kolekcję obiektów wizualnych.  
  
### <a name="drawing-content-in-visual-objects"></a>Zawartość rysowania w obiektach wizualnych  
 A <xref:System.Windows.Media.Visual> obiekt przechowuje dane renderowania jako **Lista instrukcji grafiki wektorowej**. Każdy element na liście instrukcji reprezentuje zestaw niskiego poziomu danymi graficznymi i skojarzonych zasobów format serializacji. Istnieją cztery różne typy danych renderowania, który może zawierać zawartość rysowania.  
  
|Typ zawartości rysowania|Opis|  
|--------------------------|-----------------|  
|Grafika wektorowa|Reprezentuje wektor danymi graficznymi i wszelkie powiązane <xref:System.Windows.Media.Brush> i <xref:System.Windows.Media.Pen> informacji.|  
|Obraz|Reprezentuje obraz w obrębie regionu definicją <xref:System.Windows.Rect>.|  
|Symbol|Reprezentuje rysunku, który renderuje <xref:System.Windows.Media.GlyphRun>, czyli sekwencji symbole z zasobu określonej czcionki. Jest to, jak przedstawić tekstu.|  
|Połączenia wideo|Reprezentuje rysunku, który renderuje wideo.|  
  
 <xref:System.Windows.Media.DrawingContext> Umożliwia wypełnienie <xref:System.Windows.Media.Visual> o zawartości wizualnej. Kiedy używasz <xref:System.Windows.Media.DrawingContext> polecenia rysowania obiektu są faktycznie przechowywania zestaw danych renderowania, który będzie później używany przez system grafiki; nie jest rysowany na ekranie w czasie rzeczywistym.  
  
 Po utworzeniu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolować, takich jak <xref:System.Windows.Controls.Button>, formant niejawnie generuje dane renderowania sam rysowania. Na przykład ustawienie <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button> powoduje, że formant do przechowywania renderowania reprezentacja symbolu.  
  
 A <xref:System.Windows.Media.Visual> opisuje jego zawartość jako jedną lub więcej <xref:System.Windows.Media.Drawing> obiektów zawartych w <xref:System.Windows.Media.DrawingGroup>. A <xref:System.Windows.Media.DrawingGroup> opisano również maski krycia, przekształcenia, efekty bitmapowe i inne operacje, które są stosowane do jego zawartości. <xref:System.Windows.Media.DrawingGroup> operacje są stosowane w następującej kolejności, gdy zawartość jest wyświetlana: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, a następnie <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Poniższa ilustracja przedstawia kolejność, w którym <xref:System.Windows.Media.DrawingGroup> operacji są stosowane podczas sekwencji renderowania.  
  
 ![DrawingGroup — kolejność operacji](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji DrawingGroup  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd obiektów rysowania](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Zawartość rysowania w warstwie Visual  
 Możesz nigdy nie bezpośrednio utworzyć wystąpienia <xref:System.Windows.Media.DrawingContext>; można jednak uzyskać rysowania kontekstu z niektórych metod, takich jak <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> i <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>. Poniższy przykład pobiera <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> i używa go, aby narysować prostokąt.  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Wyliczanie zawartości rysowania w warstwie Visual  
 Oprócz ich zastosowań <xref:System.Windows.Media.Drawing> obiektów również zapewnić model obiektu wyliczanie zawartości <xref:System.Windows.Media.Visual>.  
  
> [!NOTE]
>  Gdy wyliczają to zawartość wizualizacji, są pobierane <xref:System.Windows.Media.Drawing> obiektów i nie podstawowej reprezentacji danych renderowania jako lista instrukcji grafiki wektorowej.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, która pobierze <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i ją wyliczanie.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak obiektów wizualnych są używane do tworzenia kontrolek  
 Wiele obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składają się z innych obiektów wizualnych, co oznacza mogą zawierać różne hierarchie obiektów podrzędnych. Wiele użytkownika elementy w interfejsu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takie jak formanty, składających się z wielu obiektów wizualnych reprezentująca różne rodzaje renderowania elementów. Na przykład <xref:System.Windows.Controls.Button> formant może zawierać wiele innych obiektów, w tym <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>, <xref:System.Windows.Controls.ContentPresenter>, i <xref:System.Windows.Controls.TextBlock>.  
  
 Poniższy kod przedstawia <xref:System.Windows.Controls.Button> kontroli zdefiniowane w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Zostałby wyliczyć obiektów wizualnych, wchodzące w skład domyślnie <xref:System.Windows.Controls.Button> kontroli, czy okażą się hierarchii obiektów wizualnych, które przedstawiono poniżej:  
  
 ![Diagram hierarchii drzewa wizualnego](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.gif "VisualLayerOverview03")  
Diagram hierarchii drzewa wizualnego  
  
 <xref:System.Windows.Controls.Button> Kontrolka zawiera <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, który z kolei zawiera <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element jest odpowiedzialne za narysowanie obramowania i tło <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ContentPresenter> Element jest odpowiedzialny za wyświetlania zawartości <xref:System.Windows.Controls.Button>. W takim przypadku od wyświetlanie tekstu, <xref:System.Windows.Controls.ContentPresenter> element zawiera <xref:System.Windows.Controls.TextBlock> elementu. Fakt, <xref:System.Windows.Controls.Button> kontrolować używa <xref:System.Windows.Controls.ContentPresenter> oznacza, że zawartość mogą być reprezentowane przez inne elementy, takie jak <xref:System.Windows.Controls.Image> lub geometrii, takie jak <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Szablony kontrolek  
 Klucz do rozszerzenia kontrolki do hierarchii kontroli jest <xref:System.Windows.Controls.ControlTemplate>. Szablon kontrolki określa domyślna hierarchia wizualnych dla formantu. Gdy odwołujesz się jawnie kontrolki, możesz niejawnie odwoływać się hierarchii visual. Możesz przesłonić wartości domyślne dla szablonu kontrolki do utworzenia dostosowanego wyglądu kontrolki. Na przykład, można zmodyfikować wartości koloru tła <xref:System.Windows.Controls.Button> kontroli, tak aby używał zamiast wartości koloru wartość koloru gradientu liniowego. Aby uzyskać więcej informacji, zobacz [style i szablony przycisków](../../../../docs/framework/wpf/controls/button-styles-and-templates.md).  
  
 To interfejs użytkownika elementu, takie jak <xref:System.Windows.Controls.Button> sterowania, zawiera kilka wektor grafiki instrukcji list, które opisują definicji całego renderowania formantu. Poniższy kod przedstawia <xref:System.Windows.Controls.Button> kontroli zdefiniowane w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Gdyby wyliczyć obiektów wizualnych i wektorowej listy instrukcji grafiki, wchodzące w skład <xref:System.Windows.Controls.Button> kontroli, czy okażą się hierarchię obiektów, które przedstawiono poniżej:  
  
 ![Diagram drzewa wizualnego i danych renderowania](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
Diagram drzewa wizualnego i danych renderowania  
  
 <xref:System.Windows.Controls.Button> Kontrolka zawiera <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, który z kolei zawiera <xref:System.Windows.Controls.ContentPresenter> elementu. <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> Element jest odpowiedzialne za narysowanie wszystkie dyskretnych elementy, które tworzą obramowania i tło przycisku. <xref:System.Windows.Controls.ContentPresenter> Element jest odpowiedzialny za wyświetlania zawartości <xref:System.Windows.Controls.Button>. W takim przypadku od wyświetlanie obrazów, <xref:System.Windows.Controls.ContentPresenter> element zawiera <xref:System.Windows.Controls.Image> elementu.  
  
 Istnieje kilka punktów, należy pamiętać o hierarchii obiektów wizualnych i listy instrukcji grafiki wektorowej:  
  
-   Kolejność w hierarchii reprezentuje kolejność renderowania pobieranie informacji. Z głównego elementu wizualnego jest przesunięta elementów podrzędnych, od lewej do prawej i od góry do dołu. Jeśli element ma elementy podrzędne wizualnych, są one przechodni przed elementy równorzędne.  
  
-   Elementy innego niż liść węzła w hierarchii, takie jak <xref:System.Windows.Controls.ContentPresenter>, są używane do zawierać elementy podrzędne — nie zawierają listy instrukcji.  
  
-   Jeśli element graficzny zawiera listę instrukcji grafiki wektorowej i wizualne elementy podrzędne, listy instrukcji w nadrzędnego elementu wizualnego jest renderowany przed rysunków w jednym z obiektów wizualnych podrzędnych.  
  
-   Elementy na liście instrukcji grafiki wektorowej są renderowane od lewej do prawej.  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>Drzewo wizualne  
 Drzewo wizualne zawiera wszystkie elementy wizualne, używany w interfejsie użytkownika aplikacji. Ponieważ utrwalonych pobieranie informacji nie zawiera elementu wizualnego, można traktować poziomu drzewa wizualnego jako wykres scen, zawierający wszystkie informacje renderowania potrzebne do tworzenia danych wyjściowych do urządzenia. To drzewo stanowi nagromadzenie wszystkich elementów wizualnych utworzonych bezpośrednio przez aplikację, czy w kodzie lub w znacznikach. Drzewo wizualne zawiera również wszystkie elementy wizualne utworzone przez rozszerzenie szablonu elementów takich jak formanty i obiekty danych.  
  
 Poniższy kod przedstawia <xref:System.Windows.Controls.StackPanel> elementu zdefiniowanego w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Jeśli masz zamiar wyliczyć obiektów wizualnych, wchodzące w skład <xref:System.Windows.Controls.StackPanel> elementu w przykładzie znaczników, czy okażą się hierarchii obiektów wizualnych, które przedstawiono poniżej:  
  
 ![Diagram hierarchii drzewa wizualnego](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.gif "VisualLayerOverview05")  
Diagram hierarchii drzewa wizualnego  
  
### <a name="rendering-order"></a>Kolejność renderowania  
 Drzewo wizualne określa kolejność renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów wizualnych i rysowania. Kolejność przechodzenia rozpoczyna się od katalogu głównego wizualizację, która jest najbardziej na wierzchu węzeł w drzewie wizualnym. Dzieci wizualizacji główny jest następnie przesunięta, od lewej do prawej. Jeśli wizualizacja ma elementy podrzędne, jego elementów podrzędnych jest przesunięta przed elementami równorzędnymi elementu wizualnego. Oznacza to, że zawartość elementu podrzędnego visual jest renderowany przed zawartością elementu wizualnego.  
  
 ![Diagram kolejności renderowania w drzewie wizualnym](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.gif "VisualLayerOverview06")  
Diagram przedstawiający kolejność renderowania drzewo wizualne  
  
### <a name="root-visual"></a>Główny Visual  
 **Głównego visual** jest umieszczony najwyżej elementu w hierarchii drzewa wizualnego. W większości aplikacji klasy bazowej głównego visual jest <xref:System.Windows.Window> lub <xref:System.Windows.Navigation.NavigationWindow>. Jednak jeśli były hosting obiektów visual w aplikacji Win32, główny visual będzie visual najważniejsze, które zostały hostingu w oknie Win32. Aby uzyskać więcej informacji, zobacz [samouczka: Hosting obiektów Visual w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relacja drzewo logiczne  
 Drzewo logiczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentuje elementów aplikacji w czasie wykonywania. Mimo że nie bezpośrednio modyfikować tego drzewa, ten widok aplikacji jest przydatne dla zrozumienia, dziedziczenie właściwości i zdarzenia, routing. W przeciwieństwie do drzewa wizualnego drzewa logicznego może reprezentować obiektów danych innym niż wizualny, taki jak <xref:System.Windows.Documents.ListItem>. W wielu przypadkach drzewo logiczne ściśle mapuje do definicji znaczników aplikacji. Poniższy kod przedstawia <xref:System.Windows.Controls.DockPanel> elementu zdefiniowanego w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Zostałby wyliczyć logicznymi obiektami, które obejmują <xref:System.Windows.Controls.DockPanel> elementu w przykładzie znaczników, czy okażą się hierarchii logicznymi obiektami, które przedstawiono poniżej:  
  
 ![Diagram drzewa](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.gif "Tree1_wcp")  
Diagram przedstawiający drzewo logiczne  
  
 Drzewo wizualne i drzewo logiczne są synchronizowane z bieżącego zestawu elementów aplikacji, odzwierciedlenie wszelkich dodawania, usuwania lub modyfikowania elementów. Jednak drzew przedstawiają różne widoki aplikacji. W przeciwieństwie do drzewa wizualnego drzewa logicznego nie jest powiększony kontrolki <xref:System.Windows.Controls.ContentPresenter> elementu. Oznacza to, że nie ma bezpośredniego relację między drzewo logiczne i drzewa wizualnego do tego samego zestawu obiektów. W rzeczywistości wywoływania **LogicalTreeHelper** obiektu <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> metody i **VisualTreeHelper** obiektu <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> przy użyciu tego samego elementu, ponieważ parametr daje różne wyniki — metoda .  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Wyświetlanie drzewa wizualnego, za pomocą edytor XamlPad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Narzędzia edytor XamlPad, udostępnia opcję umożliwiające wyświetlanie i eksploracji drzewa wizualnego, który odnosi się do aktualnie zdefiniowanych [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zawartości. Kliknij przycisk **Pokaż drzewa wizualnego** przycisk na pasku menu, aby wyświetlić drzewo wizualne. Poniższy rysunek ilustruje rozszerzenie [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zawartość w węzłach drzewa wizualnego w **wizualnego drzewa Eksploratora** panelu edytor XamlPad:  
  
 ![Panel Eksploratora drzewa wizualnego w edytor XamlPad](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
Panel Eksploratora drzewa wizualnego w edytor XamlPad  
  
 Zwróć uwagę sposób, w jaki <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, i <xref:System.Windows.Controls.Button> formantów każdego wyświetlić hierarchię oddzielny obiekt wizualny w **wizualnego drzewa Eksploratora** panelu edytor XamlPad. Jest to spowodowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty mają <xref:System.Windows.Controls.ControlTemplate> zawiera drzewo wizualne tej kontrolki. Gdy odwołujesz się jawnie kontrolki, możesz niejawnie odwoływać się hierarchii visual.  
  
### <a name="profiling-visual-performance"></a>Profilowanie wydajności Visual  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia zestaw narzędzi, które umożliwiają analizowanie zachowania w czasie wykonywania aplikacji i określ typy tych optymalizacji wydajności, które można zastosować profilowania wydajności. Narzędzie Profiler wizualny zapewnia rozbudowane, graficzny widok danych dotyczących wydajności przez mapowanie bezpośrednio do drzewa wizualnego w aplikacji. W tym zrzucie ekranu **użycie procesora CPU** części Visual Profiler umożliwia dokładne podział użycia obiektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług, takich jak układ i renderowania.  
  
 ![Profiler wizualny wyświetlić dane wyjściowe](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Wizualne dane wyjściowe Profiler  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>Zachowanie renderowania wizualnego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadzono kilka funkcji, które mają wpływ na zachowanie renderowania obiektów wizualnych: zachowane tryb grafiki, grafiki wektorowej i grafiki niezależnie od urządzenia.  
  
### <a name="retained-mode-graphics"></a>Tryb zachowanej grafiki  
 Jeden z kluczy do zrozumienia roli obiekt wizualny jest zrozumieć różnicę między **tryb natychmiastowy** i **przechowywane tryb** systemy graficzne. Standardowa aplikacja Win32 na podstawie GDI lub GDI + używa systemu grafiki w trybie natychmiastowym. Oznacza to, że aplikacja jest odpowiedzialna za odświeżenie część obszaru klienckiego, który zostaje unieważniony z powodu akcja, taka jak okna zmiany rozmiaru, lub zmiana jego wygląd obiektu.  
  
 ![Diagram sekwencji renderowania Win32](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Diagram sekwencji renderowania Win32  
  
 Z kolei [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] korzysta z zachowanej trybu systemu. Oznacza to, że obiektów aplikacji, które mają wygląd definiują zestaw serializacji danych rysunku. Po zdefiniowaniu rysowania danych system jest odpowiedzialny po tej dacie odpowiadanie na wszystkie żądania repaint renderowania obiektów aplikacji. Nawet w czasie wykonywania można zmodyfikować lub utworzyć obiekty aplikacji i nadal korzystają z systemu pod kątem odpowiada na żądania malowania. Zasilania w systemie grafiki zachowanej tryb jest, czy rysowanie informacji jest zawsze utrwalony w Zserializowany stan aplikacji, ale odpowiedzialność renderowania od lewej do systemu. Na poniższym diagramie przedstawiono, jak aplikacja zależy od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reagowania namalować żądań.  
  
 ![Diagram sekwencji renderowania WPF](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
Diagram sekwencji renderowania WPF  
  
#### <a name="intelligent-redrawing"></a>Inteligentne ponownego narysowania  
 Jedną z największych zalet używania trybu zachowanej grafiki jest to, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] efektywnie można zoptymalizować, czego potrzebuje do narysowania w aplikacji. Nawet, jeśli masz złożone sceny z różnymi poziomami nieprzezroczystość, zazwyczaj nie trzeba napisać kod specjalnych zoptymalizować ponownego narysowania. Porównaj to dzięki programowaniu Win32, w którym możesz poświęcić wiele wysiłku w optymalizacji aplikacji, minimalizując ilość osadzeniu w regionie aktualizacji. Zobacz [osadzeniu w regionie aktualizacji](/windows/desktop/gdi/redrawing-in-the-update-region) przykład typu złożoności związane z optymalizacją, odświeżanie w aplikacji Win32.  
  
### <a name="vector-graphics"></a>Grafika wektorowa  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa **grafika wektorowa** jako formatem renderowania danych. Grafika wektorowa — które obejmują skalowalne grafiki wektorowej (SVG), Windows metaplików (WMF) i czcionki TrueType — przechowywanie danych renderowania i przesłać je jako listę instrukcji, które opisują jak odtworzyć z obrazu przy użyciu podstawowych grafiki. Na przykład czcionki TrueType są konspektu czcionek, które opisują zestaw linii, krzywych i poleceń, a nie tablicę pikseli. Jedną z najważniejszych korzyści zapewnianych przez grafiki wektorowej jest możliwość skalowania do dowolnego rozmiaru i rozdzielczości.  
  
 W przeciwieństwie do grafiki wektorowej grafiki mapy bitowej do przechowywania danych renderowania jako reprezentację poszczególne piksele obrazu wstępnie renderowanych dla określonego rozwiązania. Jedną z najważniejszych różnic między formaty graficzne mapy bitowej i wektora jest wierności do oryginalnego obrazu źródłowego. Na przykład po zmodyfikowaniu rozmiar obrazu źródłowego, systemy graficzne mapy bitowej obraz jest rozciągany, natomiast systemów grafiki wektorowej, skaluje obraz zachowaniu jakości obrazu.  
  
 Poniższa ilustracja przedstawia obrazu źródłowego, który został zmieniony przez 300%. Zwróć uwagę, zakłócenia, które są wyświetlane, gdy obraz źródłowy jest rozciągana jako obraz mapy bitowej grafiki zamiast skalować jako obraz grafiki wektorowej.  
  
 ![Różnice między grafiki wektorowej i rastrowych](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
Różnice między grafiki wektorowej i rastrowe  
  
 Następujący kod przedstawia dwa <xref:System.Windows.Shapes.Path> elementy zdefiniowane. Drugi element używa <xref:System.Windows.Media.ScaleTransform> zmiany rozmiaru instrukcje rysowania pierwszego elementu przez 300%. Należy zauważyć, że instrukcje rysowania w <xref:System.Windows.Shapes.Path> elementy pozostają niezmienione.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Rozdzielczość i niezależny od urządzenia grafiki — informacje  
 Istnieją dwa czynniki systemu, które określają rozmiar tekstu i grafiki na ekranie: rozdzielczość i rozdzielczości DPI. Rozdzielczość w tym artykule opisano liczbę pikseli, które są wyświetlane na ekranie. Jak wyższa rozdzielczość jeszcze mniejsze, powodując grafiki i tekstu, aby wydawać się mniejsza. Grafiki wyświetlany na monitorze, który został ustawiony na 1024 x 768 będą wyświetlane znacznie mniejszy, gdy rozwiązanie jest zmieniana na 1600 x 1200.  
  
 Inne ustawienia systemowego DPI, w tym artykule opisano rozmiar CAL ekranu, w pikselach. Większość [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemy mają rozdzielczości 96, co oznacza CAL ekranu jest 96 pikseli. Zwiększanie ustawienia DPI sprawia, że większy; CAL ekranu Zmniejsza to wartość DPI sprawia, że CAL ekranu mniejsze. Oznacza to, że CAL ekranu nie jest taki sam rozmiar jak cal rzeczywistych; w większości systemów, prawdopodobnie nie jest. Zwiększenie wartości DPI obsługującą ustawienia DPI grafiki i tekstu wydają się większe, ponieważ została zwiększona rozmiar CAL ekranu. Zwiększenie wartości DPI może ułatwić tekstu do odczytania, zwłaszcza w wysokiej rozdzielczości.  
  
 Nie wszystkie aplikacje są obsługującą ustawienia DPI: niektóre wykorzystują pikseli sprzętu jako podstawowa jednostka miary; Zmiana rozdzielczości DPI systemu nie ma wpływu na te aplikacje. Wiele innych aplikacji użyj obsługującą ustawienia DPI jednostki opisują rozmiary czcionek, ale umożliwia opisano wszystkie inne piksele. Zbyt małej lub zbyt duży, dzięki czemu to wartość DPI może spowodować problemy związane z układem dla tych aplikacji, ponieważ tekst aplikacji skaluje się ustawienie rozdzielczości DPI systemu, ale nie ma interfejsu użytkownika aplikacji. Ten problem został wyeliminowany dla aplikacji utworzonych za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje automatyczne skalowanie przy użyciu pikseli niezależnie od urządzenia jako jego podstawowy jednostkę, zamiast pikseli, najlepiej sprzętu grafiki i tekstu skalowanie poprawnie, bez konieczności wykonywania dodatkowej pracy od dewelopera aplikacji. Na poniższej ilustracji przedstawiono przykładowy sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tekstu i grafiki są wyświetlane na różne ustawienia DPI.  
  
 ![Grafika i tekstowych w miejscach występowania różne ustawienia DPI](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika i tekstowych w miejscach występowania różne ustawienia DPI  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>VisualTreeHelper Class  
 <xref:System.Windows.Media.VisualTreeHelper> Klasy jest statyczną klasę pomocy dostarczająca funkcje niskiego poziomu dla programowania na poziomie obiekt wizualny, co jest przydatne w bardzo konkretnych scenariuszy, takich jak tworzenie niestandardowych kontrolek o wysokiej wydajności. W przypadku większości wyższego poziomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework obiekty, takie jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.TextBlock>, oferuje większą elastyczność i łatwość użycia.  
  
### <a name="hit-testing"></a>Test trafienia  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa dostarcza metody do testowania w obiektach wizualnych po naciśnięciu domyślną obsługę testów trafienia nie spełnia Twoich potrzeb. Możesz użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody <xref:System.Windows.Media.VisualTreeHelper> klasę, aby określić, czy wartość współrzędnych geometrii lub punkt znajduje się w granicy danego obiektu, takiego jak kontrolka lub element graficzny. Na przykład można użyć testowania trafień w celu określenia, czy kliknięcia w ramach prostokąt otaczający obiektu mieści się w geometrii koła, możesz także Przesłoń domyślną implementację elementu trafień test, aby wykonać swoje własne niestandardowe test trafień obliczenia.  
  
 Aby uzyskać więcej informacji na temat testowania trafień, zobacz [trafień testowania w warstwie wizualnej](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Wyliczanie drzewo wizualne  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa udostępnia funkcje wyliczanie elementów członkowskich drzewo wizualne. Aby pobrać element nadrzędny, należy wywołać <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metody. Do pobrania, potomnego lub podrzędnego bezpośrednich, visual obiektu, wywołaj <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metody. Metoda ta zwraca element podrzędny <xref:System.Windows.Media.Visual> nadrzędnego elementu pod określonym indeksem.  
  
 Poniższy przykład pokazuje, jak wyliczyć wszystkie elementy podrzędne obiektu visual to technika, które można użyć, jeśli interesują Cię serializacji wszystkie informacje renderowania hierarchii obiekt wizualny.  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 W większości przypadków drzewo logiczne jest bardziej użytecznej reprezentacji elementów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Mimo że nie należy bezpośrednio modyfikować drzewo logiczne, ten widok aplikacji jest przydatne dla zrozumienia, dziedziczenie właściwości i zdarzenia, routing. W przeciwieństwie do drzewa wizualnego drzewa logicznego może reprezentować obiektów danych innym niż wizualny, taki jak <xref:System.Windows.Documents.ListItem>. Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
 <xref:System.Windows.Media.VisualTreeHelper> Klasa dostarcza metody do zwracania prostokąt otaczający obiektów wizualnych. Prostokąt otaczający obiekt wizualny można zwrócić przez wywołanie metody <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Może zwracać prostokąt otaczający wszystkie elementy podrzędne obiektu visual visual sam obiekt, w tym przez wywołanie metody <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>. Poniższy kod pokazuje, jak można obliczyć prostokąt otaczający obiekt wizualny i wszystkie jego elementy podrzędne.  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Test trafienia w warstwie wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
- [Użycie obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
- [Samouczek: Hosting obiektów Visual w aplikacji Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
