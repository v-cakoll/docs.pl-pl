---
title: Przegląd Panele
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187577"
---
# <a name="panels-overview"></a>Przegląd Panele
<xref:System.Windows.Controls.Panel>elementy są komponentami, które kontrolują renderowanie elementów — ich rozmiar i wymiary, ich położenie i rozmieszczenie zawartości podrzędnej. Zapewnia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] szereg wstępnie zdefiniowanych <xref:System.Windows.Controls.Panel> elementów, a także możliwość <xref:System.Windows.Controls.Panel> konstruowania elementów niestandardowych.  
  
 Ten temat zawiera poniższe sekcje.  
  
- [Klasa panelu](#Panels_view_from_10000_feet)  
  
- [Elementy panelu Wspólnych Członków](#Panels_declared_members)  
  
- [Elementy panelu pochodnego](#Panels_derived_elements)  
  
- [Panele interfejsu użytkownika](#Panels_main_UI_elements)  
  
- [Zagnieżdżone elementy panelu](#Panels_nested_panel_elements)  
  
- [Elementy panelu niestandardowego](#Panels_custom_panel_elements)  
  
- [Obsługa lokalizacji/globalizacji](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>Klasa panelu  
 <xref:System.Windows.Controls.Panel>jest klasą podstawową dla wszystkich [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]elementów, które zapewniają obsługę układu w programie . Elementy <xref:System.Windows.Controls.Panel> pochodne są używane do [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pozycjonować i rozmieszczać elementy w i kod.  
  
 Zawiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kompleksowy zestaw implementacji paneli pochodnych, które umożliwiają wiele złożonych układów. Te klasy pochodne uwidaczniają właściwości [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i metody, które umożliwiają większość standardowych scenariuszy. Deweloperzy, którzy nie są w stanie znaleźć zachowanie układu podrzędnego, <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> który <xref:System.Windows.FrameworkElement.MeasureOverride%2A> spełnia ich potrzeby można utworzyć nowe układy, zastępując i metody. Aby uzyskać więcej informacji na temat zachowań układu niestandardowego, zobacz [Elementy panelu niestandardowego](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Członkowie panelu  
 Wszystkie <xref:System.Windows.Controls.Panel> elementy obsługują podstawowe właściwości rozmiaru i <xref:System.Windows.FrameworkElement>pozycjonowania zdefiniowane przez , w tym <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, , <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>i <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Aby uzyskać dodatkowe informacje na <xref:System.Windows.FrameworkElement>temat właściwości pozycjonowania zdefiniowanych przez , zobacz [Wyrównanie, Marginesy i Omówienie dopełnienia](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>udostępnia dodatkowe właściwości, które mają kluczowe znaczenie w zrozumieniu i użyciu układu. Właściwość <xref:System.Windows.Controls.Panel.Background%2A> służy do wypełniania obszaru między granicami pochodnego <xref:System.Windows.Media.Brush>elementu panelu za pomocą pliku . <xref:System.Windows.Controls.Panel.Children%2A>reprezentuje podrzędną kolekcję <xref:System.Windows.Controls.Panel> elementów, z których składa się. <xref:System.Windows.Controls.Panel.InternalChildren%2A>reprezentuje zawartość kolekcji oraz <xref:System.Windows.Controls.Panel.Children%2A> tych elementów członkowskich generowanych przez powiązanie danych. Oba składają <xref:System.Windows.Controls.UIElementCollection> się z elementów podrzędnych hostowanych w obrębie obiektu nadrzędnego. <xref:System.Windows.Controls.Panel>  
  
 Panel udostępnia również <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> dołączoną właściwość, która może służyć do <xref:System.Windows.Controls.Panel>uzyskania kolejności warstwowej w pochodnym . Członkowie <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu o wyższej <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartości pojawiają się przed <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> członkami o niższej wartości. Jest to szczególnie przydatne w <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Grid> przypadku paneli, takich jak i które umożliwiają dzieciom współdzielenie tej samej przestrzeni współrzędnych.  
  
 <xref:System.Windows.Controls.Panel>definiuje również <xref:System.Windows.Controls.Panel.OnRender%2A> metodę, która może służyć do zastępowania domyślnego <xref:System.Windows.Controls.Panel>zachowania prezentacji pliku .  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Pochodne elementy panelu szeroko wykorzystują dołączone właściwości. Dołączone właściwość jest wyspecjalizowaną formą właściwości zależności, która nie ma właściwości "otoka" właściwości common language runtime (CLR). Dołączone właściwości mają wyspecjalizowaną składnię w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], co można zobaczyć w kilku przykładach, które następują.  
  
 Jednym z celów dołączonej właściwości jest umożliwienie elementów podrzędnych do przechowywania unikatowych wartości właściwości, która jest faktycznie zdefiniowana przez element nadrzędny. Aplikacja tej funkcji jest o elementy podrzędne poinformować rodzica, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]jak chcą być prezentowane w , co jest niezwykle przydatne dla układu aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie załączonych właściwości](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>Elementy panelu pochodnego  
 Wiele obiektów pochodzi <xref:System.Windows.Controls.Panel>z , ale nie wszystkie z nich są przeznaczone do użycia jako dostawców układu głównego. Istnieje sześć zdefiniowanych<xref:System.Windows.Controls.Canvas>klas <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>paneli <xref:System.Windows.Controls.VirtualizingStackPanel>( <xref:System.Windows.Controls.WrapPanel>, , <xref:System.Windows.Controls.StackPanel>, , , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]i ), które są zaprojektowane specjalnie do tworzenia aplikacji.  
  
 Każdy element panelu hermetyzuje własną specjalną funkcjonalność, jak przedstawiono w poniższej tabeli.  
  
|Nazwa elementu|Panel interfejsu użytkownika?|Opis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Tak|Definiuje obszar, w którym można jawnie umieszczać elementy <xref:System.Windows.Controls.Canvas> podrzędne przez współrzędne względem obszaru.|  
|<xref:System.Windows.Controls.DockPanel>|Tak|Definiuje obszar, w którym można rozmieszczać elementy podrzędne poziomo lub pionowo względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Tak|Definiuje elastyczny obszar siatki składający się z kolumn i wierszy. Elementy podrzędne <xref:System.Windows.Controls.Grid> a mogą być umieszczone <xref:System.Windows.FrameworkElement.Margin%2A> dokładnie za pomocą właściwości.|  
|<xref:System.Windows.Controls.StackPanel>|Tak|Rozmieszcza elementy podrzędne w jedną linię, która może być zorientowana poziomo lub pionowo.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Nie|Obsługuje układ przycisków kart <xref:System.Windows.Controls.TabControl>w pliku .|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nie|Rozmieszcza zawartość <xref:System.Windows.Controls.ToolBar> w formancie.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Nie|<xref:System.Windows.Controls.Primitives.UniformGrid>służy do rozmieszczenia obrażeń podrzędnych w siatce o równych rozmiarach komórek.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Nie|Zapewnia klasę podstawową dla paneli, które można "wirtualizować" ich kolekcji elementów podrzędnych.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Tak|Rozmieszcza i wirtualizuje zawartość w jednej linii zorientowanej poziomo lub pionowo.|  
|<xref:System.Windows.Controls.WrapPanel>|Tak|<xref:System.Windows.Controls.WrapPanel>umieszcza elementy podrzędne w pozycji sekwencyjnej od lewej do prawej, przebijając zawartość do następnego wiersza na krawędzi pola zawierającego. Kolejne zamawianie odbywa się sekwencyjnie od góry do dołu <xref:System.Windows.Controls.WrapPanel.Orientation%2A> lub od prawej do lewej, w zależności od wartości właściwości.|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>Panele interfejsu użytkownika  
 Dostępnych jest sześć klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paneli, które [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są <xref:System.Windows.Controls.Canvas>zoptymalizowane pod kątem scenariuszy obsługi: , <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, i <xref:System.Windows.Controls.WrapPanel>. Te elementy panelu są łatwe w użyciu, wszechstronne i rozszerzalne w większości zastosowań.  
  
 Każdy element <xref:System.Windows.Controls.Panel> pochodny traktuje ograniczenia zmiany rozmiaru inaczej. Zrozumienie, <xref:System.Windows.Controls.Panel> jak obsługuje wiązania w kierunku poziomym lub pionowym, może sprawić, że układ stanie się bardziej przewidywalny.  
  
|**Nazwa panelu**|**x wymiar**|**wymiar y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Ograniczone do zawartości|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.DockPanel>|Ograniczone|Ograniczone|  
|<xref:System.Windows.Controls.StackPanel>(Orientacja pionowa)|Ograniczone|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.StackPanel>(Orientacja pozioma)|Ograniczone do zawartości|Ograniczone|  
|<xref:System.Windows.Controls.Grid>|Ograniczone|Ograniczone, z wyjątkiem <xref:System.Windows.GridUnitType.Auto> przypadków, w których stosuje się do wierszy i kolumn|  
|<xref:System.Windows.Controls.WrapPanel>|Ograniczone do zawartości|Ograniczone do zawartości|  
  
 Bardziej szczegółowe opisy i przykłady użycia każdego z tych elementów można znaleźć poniżej.  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>Kanwa  
 Element <xref:System.Windows.Controls.Canvas> umożliwia pozycjonowanie zawartości zgodnie z bezwzględnymi współrzędnymi *x-* i *y.* Elementy mogą być rysowane w unikalnym miejscu; lub, jeśli elementy zajmują te same współrzędne, kolejność, w jakiej pojawiają się w znacznikach określa kolejność rysowania elementów.  
  
 <xref:System.Windows.Controls.Canvas>zapewnia najbardziej elastyczną obsługę <xref:System.Windows.Controls.Panel>układu spośród wszystkich . Właściwości Wysokość i Szerokość służą do definiowania obszaru kanwy, a elementy wewnątrz są przypisywane <xref:System.Windows.Controls.Canvas>współrzędne bezwzględne względem obszaru nadrzędnego . Cztery dołączone właściwości, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, i , umożliwiają precyzyjną kontrolę rozmieszczenia obiektu w <xref:System.Windows.Controls.Canvas>obrębie , umożliwiając deweloperowi położenie i rozmieszczenie elementów dokładnie na ekranie.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds w obrębie kanwy  
 <xref:System.Windows.Controls.Canvas>elementy podrzędne można umieszczać w dowolnej pozycji na ekranie, <xref:System.Windows.FrameworkElement.Height%2A> nawet <xref:System.Windows.FrameworkElement.Width%2A>w współrzędnych, które znajdują się poza jego własnym zdefiniowanym i . Ponadto, <xref:System.Windows.Controls.Canvas> nie ma wpływu na wielkość swoich dzieci. W rezultacie element podrzędny może przerysować inne elementy poza prostokątem ograniczającym <xref:System.Windows.Controls.Canvas>nadrzędnego . Domyślnym zachowaniem <xref:System.Windows.Controls.Canvas> a jest umożliwienie obrażeń podrzędnych, <xref:System.Windows.Controls.Canvas>które mają być rysowane poza granicami nadrzędnego . Jeśli to zachowanie jest <xref:System.Windows.UIElement.ClipToBounds%2A> niepożądane, właściwość można ustawić na `true`. Powoduje <xref:System.Windows.Controls.Canvas> to, że klip do własnego rozmiaru. <xref:System.Windows.Controls.Canvas>jest jedynym elementem układu, który umożliwia elementy podrzędne, które mają być rysowane poza jego granicami.  
  
 To zachowanie jest graficznie zilustrowane w [przykładzie porównania właściwości szerokości](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
#### <a name="defining-and-using-a-canvas"></a>Definiowanie i używanie kanwy  
 A <xref:System.Windows.Controls.Canvas> można utworzyć wystąpienia po [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] prostu przy użyciu kodu lub kodu. W poniższym przykładzie <xref:System.Windows.Controls.Canvas> pokazano, jak używać do absolutnie pozycjonowania zawartości. Ten kod tworzy trzy kwadraty 100 pikseli. Pierwszy kwadrat jest czerwony, a jego górna lewa pozycja *(x, y)* jest określona jako (0, 0). Drugi kwadrat jest zielony, a jego górna lewa pozycja to (100, 100), tuż poniżej i po prawej stronie pierwszego kwadratu. Trzeci kwadrat jest niebieski, a jego górna lewa pozycja jest (50, 50), obejmując w ten sposób prawy dolny kwadrant pierwszego kwadratu i górny lewy kwadrant drugiego. Ponieważ trzeci kwadrat jest rozplanowany jako ostatni, wydaje się być na dwóch pozostałych kwadratach — oznacza to, że nakładające się fragmenty zakładają kolor trzeciego pola.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nowy, który wygląda tak.  
  
 ![Typowy element kanwy.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 Element <xref:System.Windows.Controls.DockPanel> używa dołączonej <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> właściwości jako zestaw w elementach zawartości podrzędnej do pozycjonowania zawartości wzdłuż krawędzi kontenera. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest <xref:System.Windows.Controls.Dock.Top> ustawiona lub <xref:System.Windows.Controls.Dock.Bottom>, umieszcza elementy podrzędne powyżej lub poniżej siebie. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest <xref:System.Windows.Controls.Dock.Left> ustawiona lub <xref:System.Windows.Controls.Dock.Right>, umieszcza elementy podrzędne po lewej lub prawej stronie siebie. Właściwość <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> określa położenie elementu końcowego dodanego jako <xref:System.Windows.Controls.DockPanel>element podrzędny .  
  
 Można użyć <xref:System.Windows.Controls.DockPanel> do umieszczenia grupy powiązanych formantów, takich jak zestaw przycisków. Alternatywnie, można go użyć do utworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]"paned" , podobne do tego, który znajduje się w programie Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Zmiana rozmiaru do zawartości  
 Jeśli <xref:System.Windows.FrameworkElement.Height%2A> jego <xref:System.Windows.FrameworkElement.Width%2A> i właściwości nie <xref:System.Windows.Controls.DockPanel> są określone, rozmiary do jego zawartości. Rozmiar można zwiększyć lub zmniejszyć, aby pomieścić rozmiar jego elementów podrzędnych. Jednak gdy te właściwości są określone i nie ma już miejsca <xref:System.Windows.Controls.DockPanel> dla następnego określonego elementu podrzędnego, nie wyświetla tego elementu podrzędnego lub kolejnych elementów podrzędnych i nie mierzy kolejnych elementów podrzędnych.  
  
#### <a name="lastchildfill"></a>Lastchildfill  
 Domyślnie ostatni element podrzędny <xref:System.Windows.Controls.DockPanel> elementu "wypełni" pozostałe, nieprzydzielone miejsce. Jeśli to zachowanie nie jest <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> pożądane, ustaw właściwość na `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definiowanie i używanie panelu DockPanel  
 W poniższym przykładzie pokazano, <xref:System.Windows.Controls.DockPanel>jak podzielić miejsce za pomocą pliku . Pięć <xref:System.Windows.Controls.Border> elementów są dodawane <xref:System.Windows.Controls.DockPanel>jako elementy podrzędne rodzica . Każdy używa innej właściwości pozycjonowania <xref:System.Windows.Controls.DockPanel> do przestrzeni partycji. Ostatni element "wypełnia" pozostałe, nieprzydzielone miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nowy, który wygląda tak.  
  
 ![Typowy scenariusz DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Siatka  
 Element <xref:System.Windows.Controls.Grid> scala funkcjonalność bezwzględnego pozycjonowania i kontroli danych tabelaryczne. A <xref:System.Windows.Controls.Grid> umożliwia łatwe pozycjonowanie i stylowanie elementów. <xref:System.Windows.Controls.Grid>umożliwia definiowanie elastycznych grupowania wierszy i kolumn, a nawet zapewnia <xref:System.Windows.Controls.Grid> mechanizm udostępniania informacji o wielkości między wieloma elementami.  
  
#### <a name="how-is-grid-different-from-table"></a>Czym różni się siatka od tabeli?  
 <xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> dzielić niektóre typowe funkcje, ale każdy jest najlepiej nadaje się do różnych scenariuszy. A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w ramach zawartości przepływu (zobacz [Omówienie dokumentu przepływu, aby](../advanced/flow-document-overview.md) uzyskać więcej informacji na temat zawartości przepływu). Siatki są najlepiej używane wewnątrz formularzy (w zasadzie w dowolnym miejscu poza zawartością przepływu). W <xref:System.Windows.Documents.FlowDocument>obrębie <xref:System.Windows.Documents.Table> , obsługuje zachowania zawartości przepływu, takie jak podział na <xref:System.Windows.Controls.Grid> strony, ponowne wlanie kolumny i wybór zawartości, podczas gdy nie. A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej jest <xref:System.Windows.Documents.FlowDocument> używany poza <xref:System.Windows.Controls.Grid> a z wielu powodów, <xref:System.Windows.Documents.Table> w tym dodaje elementy oparte na indeksie wiersza i kolumny, nie. Element <xref:System.Windows.Controls.Grid> umożliwia nakładanie warstw zawartości podrzędnej, dzięki czemu więcej niż jeden element istnieje w pojedynczej "komórce". <xref:System.Windows.Documents.Table>nie obsługuje nakładania warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> a mogą być absolutnie umieszczone względem obszaru ich "komórki" granice. <xref:System.Windows.Documents.Table>nie obsługuje tej funkcji. Wreszcie, <xref:System.Windows.Controls.Grid> jest lżejszy <xref:System.Windows.Documents.Table>niż .  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Zachowanie rozmiaru kolumn i wierszy  
 Kolumny i wiersze zdefiniowane w a <xref:System.Windows.Controls.Grid> można skorzystać z <xref:System.Windows.GridUnitType.Star> rozmiaru w celu proporcjonalnego rozmieszczenia pozostałego miejsca. Po <xref:System.Windows.GridUnitType.Star> wybraniu jako wysokość lub szerokość wiersza lub kolumny ta kolumna lub wiersz otrzymuje ważoną część pozostałego dostępnego miejsca. Jest to w <xref:System.Windows.GridUnitType.Auto>przeciwieństwie do , który będzie rozmieszczać przestrzeń równomiernie na podstawie rozmiaru zawartości w kolumnie lub wierszu. Ta wartość jest `*` wyrażona w stanie lub `2*` podczas używania [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. W pierwszym przypadku wiersz lub kolumna otrzyma jeden raz dostępnego miejsca, w drugim przypadku dwa razy i tak dalej. Łącząc tę technikę, aby proporcjonalnie <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> rozmieścić przestrzeń z i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartość `Stretch` jest możliwe do partycjonowania przestrzeni układu przez procent miejsca na ekranie. <xref:System.Windows.Controls.Grid>jest jedynym panelem układu, który może rozmieścić przestrzeń w ten sposób.  
  
#### <a name="defining-and-using-a-grid"></a>Definiowanie i używanie siatki  
 W poniższym przykładzie pokazano, jak utworzyć [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podobny do tego znalezionego w oknie dialogowym Uruchom dostępnym w menu Start systemu Windows.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Skompilowana aplikacja daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nowy, który wygląda tak.  
  
 ![Typowy element siatki.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umożliwia "stos" elementów w wyznaczonym kierunku. Domyślny kierunek stosu jest pionowy. Właściwość <xref:System.Windows.Controls.StackPanel.Orientation%2A> może służyć do kontrolowania przepływu zawartości.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 Chociaż <xref:System.Windows.Controls.DockPanel> można również "stos" <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.StackPanel> elementy podrzędne i nie dają analogiczne wyniki w niektórych scenariuszach użycia. Na przykład kolejność elementów podrzędnych może <xref:System.Windows.Controls.DockPanel> mieć wpływ <xref:System.Windows.Controls.StackPanel>na ich rozmiar w programie . Dzieje się <xref:System.Windows.Controls.StackPanel> tak dlatego, że środki <xref:System.Double.PositiveInfinity>w <xref:System.Windows.Controls.DockPanel> kierunku układania w , podczas gdy mierzy tylko dostępny rozmiar.  
  
 W poniższym przykładzie przedstawiono tę kluczową różnicę.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Różnica w zachowaniu renderowania widać na tym obrazie.  
  
 ![Zrzut ekranu: Zrzut ekranu zdań z panelu StackPanel vs. DockPanel](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definiowanie i używanie panelu StackPanel  
 W poniższym przykładzie pokazano, jak użyć a <xref:System.Windows.Controls.StackPanel> do utworzenia zestawu przycisków umieszczonych pionowo. W przypadku pozycjonowania <xref:System.Windows.Controls.Orientation.Horizontal>poziomego ustaw właściwość na <xref:System.Windows.Controls.StackPanel.Orientation%2A> .  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Skompilowana aplikacja daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nowy, który wygląda tak.  
  
 ![Typowy element StackPanel.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>Virtualizingstackpanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]również udostępnia odmianę <xref:System.Windows.Controls.StackPanel> elementu, który automatycznie "wirtualizuje" zawartość podrzędną związaną z danymi. W tym kontekście słowo wirtualizacja odnosi się do techniki, za pomocą której podzbiór elementów są generowane z większej liczby elementów danych, na podstawie których elementy są widoczne na ekranie. Jest intensywny, zarówno pod względem pamięci i procesora, aby wygenerować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może być na ekranie w danym czasie. <xref:System.Windows.Controls.VirtualizingStackPanel>(za pomocą funkcji <xref:System.Windows.Controls.VirtualizingPanel>dostarczonych przez ) oblicza <xref:System.Windows.Controls.ItemContainerGenerator> widoczne <xref:System.Windows.Controls.ItemsControl> elementy <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListView>współpracuje z z (takich jak lub ) do tworzenia tylko elementów dla widocznych elementów.  
  
 Element <xref:System.Windows.Controls.VirtualizingStackPanel> jest automatycznie ustawiany jako host elementów <xref:System.Windows.Controls.ListBox>dla formantów, takich jak . Podczas hostowania kolekcji związanej z danymi zawartość jest automatycznie zwirtualizowane, o ile zawartość znajduje się w granicach <xref:System.Windows.Controls.ScrollViewer>. To znacznie poprawia wydajność podczas hostowania wielu elementów podrzędnych.  
  
 Poniższy znacznik pokazuje, jak <xref:System.Windows.Controls.VirtualizingStackPanel> używać jako hosta elementów. Dołączona <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> właściwość musi `true` być ustawiona na (domyślnie), aby doszło do wirtualizacji.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>służy do umieszczania elementów podrzędnych w położeniu sekwencyjnym od lewej do prawej, przebijając zawartość do następnego wiersza, gdy osiągnie krawędź kontenera nadrzędnego. Zawartość może być zorientowana poziomo lub pionowo. <xref:System.Windows.Controls.WrapPanel>jest przydatna w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przypadku prostych scenariuszy przepływu. Może być również używany do stosowania jednolitej wielkości do wszystkich elementów podrzędnych.  
  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Windows.Controls.WrapPanel> formanty do wyświetlenia, <xref:System.Windows.Controls.Button> które są zawijane, gdy dotrą do krawędzi ich kontenera.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nowy, który wygląda tak.  
  
 ![Typowy element WrapPanel.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>Zagnieżdżone elementy panelu  
 <xref:System.Windows.Controls.Panel>elementy mogą być zagnieżdżone w obrębie siebie w celu tworzenia złożonych układów. Może to okazać się bardzo <xref:System.Windows.Controls.Panel> przydatne w sytuacjach, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]gdy jeden jest idealny dla części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale może nie zaspokoić potrzeby innej części .  
  
 Nie ma praktycznego limitu ilości zagnieżdżania, które aplikacja może obsługiwać, jednak na ogół najlepiej jest ograniczyć aplikację, aby używać tylko tych paneli, które są faktycznie niezbędne dla żądanego układu. W wielu przypadkach <xref:System.Windows.Controls.Grid> element może być używany zamiast paneli zagnieżdżonych ze względu na jego elastyczność jako kontener układu. Może to zwiększyć wydajność w aplikacji, utrzymując niepotrzebne elementy z drzewa.  
  
 W poniższym przykładzie pokazano, jak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] utworzyć, <xref:System.Windows.Controls.Panel> który korzysta z zagnieżdżonych elementów w celu osiągnięcia określonego układu. W tym konkretnym <xref:System.Windows.Controls.DockPanel> przypadku element [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest używany do <xref:System.Windows.Controls.StackPanel> zapewnienia <xref:System.Windows.Controls.Grid>struktury, <xref:System.Windows.Controls.Canvas> a elementy zagnieżdżone, <xref:System.Windows.Controls.DockPanel>a , i a są używane do umieszczania elementów podrzędnych dokładnie w obrębie elementu nadrzędnego .  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Skompilowana aplikacja daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nowy, który wygląda tak.  
  
 ![Interfejs użytkownika, który korzysta z paneli zagnieżdżonych.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>Elementy panelu niestandardowego  
 Chociaż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia tablicę formantów układu elastycznego, niestandardowe zachowania układu <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> można również osiągnąć, zastępując metody i. Niestandardowe rozmiary i pozycjonowanie można osiągnąć, definiując nowe zachowania pozycjonowania w ramach tych metod zastępowania.  
  
 Podobnie niestandardowe zachowania układu oparte na klasach <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Grid>pochodnych (takich jak lub <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ) można zdefiniować przez zastąpienie ich i metod.  
  
 Poniższy znacznik pokazuje, jak utworzyć <xref:System.Windows.Controls.Panel> element niestandardowy. Ta <xref:System.Windows.Controls.Panel>nowa , `PlotPanel`zdefiniowana jako , wspiera pozycjonowanie elementów podrzędnych za pomocą zakodowanych współrzędnych *x-* i *y.* W tym przykładzie <xref:System.Windows.Shapes.Rectangle> element (nie pokazano) jest umieszczony w punkcie wydruku 50 (*x)* i 50 *(y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Aby wyświetlić bardziej złożoną implementację panelu [niestandardowego, zobacz Tworzenie przykładowego panelu zawijania zawartości niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>Obsługa lokalizacji/globalizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje szereg funkcji, które pomagają w tworzeniu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]lokalizacji.  
  
 Wszystkie elementy panelu natywnie obsługują <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość, która może służyć do dynamicznego ponownego przepływu zawartości na podstawie ustawień regionalnych lub językowych użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Właściwość <xref:System.Windows.Window.SizeToContent%2A> zapewnia mechanizm, który umożliwia deweloperom aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]przewidywanie potrzeb zlokalizowanych . Przy <xref:System.Windows.SizeToContent.WidthAndHeight> użyciu wartości tej właściwości <xref:System.Windows.Window> element nadrzędny zawsze rozmiary dynamicznie, aby dopasować zawartość i nie jest ograniczona przez sztuczne ograniczenia wysokości lub szerokości.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>i <xref:System.Windows.Controls.StackPanel> są dobre wybory [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]dla lokalizacji. <xref:System.Windows.Controls.Canvas>nie jest to jednak dobry wybór, ponieważ absolutnie pozycjonuje treści, co utrudnia lokalizowanie.  
  
 Aby uzyskać dodatkowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informacje na temat tworzenia aplikacji z interfejsami użytkownika(UI) z lokalizacjami, zobacz [omówienie użycia układu automatycznego](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Instruktaż: Moja pierwsza aplikacja komputerowa WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Przykład galerii układu WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Układ](../advanced/layout.md)
- [Przykład galerii kontrolek WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Przegląd Wyrównanie, marginesy i wypełnienia](../advanced/alignment-margins-and-padding-overview.md)
- [Tworzenie przykładowego panelu zawijania zawartości niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md)
- [Przegląd używania automatycznego układu](../advanced/use-automatic-layout-overview.md)
- [Układ i projekt](../advanced/optimizing-performance-layout-and-design.md)
