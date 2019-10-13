---
title: Panele — Omówienie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: d77ce78fe914bf300c5b33019d7cf67aa4ad74c3
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291447"
---
# <a name="panels-overview"></a>Panele — Omówienie
elementy <xref:System.Windows.Controls.Panel> to składniki kontrolujące renderowanie elementów — ich rozmiar i wymiary, ich położenie oraz układ zawartości podrzędnej. @No__t-0 udostępnia wiele wstępnie zdefiniowanych elementów <xref:System.Windows.Controls.Panel>, a także możliwość konstruowania niestandardowych elementów <xref:System.Windows.Controls.Panel>.  
  
 Ten temat zawiera następujące sekcje.  
  
- [Klasa paneli](#Panels_view_from_10000_feet)  
  
- [Wspólne elementy członkowskie elementu panelu](#Panels_declared_members)  
  
- [Elementy panelu pochodnego](#Panels_derived_elements)  
  
- [Panele interfejsu użytkownika](#Panels_main_UI_elements)  
  
- [Elementy zagnieżdżonych paneli](#Panels_nested_panel_elements)  
  
- [Elementy panelu niestandardowego](#Panels_custom_panel_elements)  
  
- [Obsługa lokalizacji/globalizacji](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Klasa paneli  
 <xref:System.Windows.Controls.Panel> jest klasą bazową dla wszystkich elementów, które zapewniają obsługę układów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Elementy pochodne <xref:System.Windows.Controls.Panel> są używane do pozycjonowania i rozmieszczania elementów w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kodzie.  
  
 @No__t-0 zawiera kompleksowy pakiet implementacji panelu pochodnego, które umożliwiają wiele złożonych układów. Te klasy pochodne uwidaczniają właściwości i metody, które umożliwiają najbardziej standardowe scenariusze [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Deweloperzy, którzy nie mogą znaleźć zachowania rozmieszczenia podrzędnego, które spełniają ich potrzeby, mogą tworzyć nowe układy, zastępując metody <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A>. Aby uzyskać więcej informacji na temat niestandardowych zachowań układu, zobacz [niestandardowe elementy panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Wspólne elementy członkowskie panelu  
 Wszystkie elementy <xref:System.Windows.Controls.Panel> obsługują podstawowe właściwości ustalania rozmiarów i położenia zdefiniowane przez <xref:System.Windows.FrameworkElement>, w tym <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> i <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Aby uzyskać dodatkowe informacje na temat właściwości pozycjonowania zdefiniowanych przez <xref:System.Windows.FrameworkElement>, zobacz [wyrównanie, marginesy i przegląd dopełnienia](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> uwidacznia dodatkowe właściwości, które mają krytyczne znaczenie w zrozumieniu i korzystaniu z układu. Właściwość <xref:System.Windows.Controls.Panel.Background%2A> służy do wypełniania obszaru między granicami elementu panelu pochodnego a <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A> reprezentuje element podrzędny kolekcji elementów, których składa się <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel.InternalChildren%2A> reprezentuje zawartość kolekcji <xref:System.Windows.Controls.Panel.Children%2A> oraz tych członków wygenerowanych przez powiązanie danych. Oba składają się z <xref:System.Windows.Controls.UIElementCollection> elementów podrzędnych hostowanych w elemencie nadrzędnym <xref:System.Windows.Controls.Panel>.  
  
 Panel udostępnia również właściwość dołączoną <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, która może służyć do osiągnięcia kolejności warstwowej w @no__t pochodnym-1. Elementy członkowskie kolekcji <xref:System.Windows.Controls.Panel.Children%2A> w panelu o wyższej wartości <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> są wyświetlane przed tymi z niższą wartością <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>. Jest to szczególnie przydatne w przypadku paneli takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.Grid>, które umożliwiają dzieciom współużytkowanie tej samej przestrzeni współrzędnych.  
  
 <xref:System.Windows.Controls.Panel> definiuje również metodę <xref:System.Windows.Controls.Panel.OnRender%2A>, która może służyć do przesłonięcia domyślnego zachowania prezentacji <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Elementy panelu pochodnego sprawiają szerokie użycie dołączonych właściwości. Dołączona właściwość to wyspecjalizowana forma właściwości zależności, która nie ma konwencjonalnej właściwości "otoka" środowiska uruchomieniowego języka wspólnego (CLR). Dołączone właściwości mają wyspecjalizowaną składnię w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], która może być widoczna w kilku przykładach.  
  
 Jednym z celów dołączonej właściwości jest umożliwienie elementom podrzędnym przechowywanie unikatowych wartości właściwości, która jest w rzeczywistości zdefiniowana przez element nadrzędny. Zastosowanie tej funkcji ma elementy podrzędne, które informują o tym, jak chcą być prezentowane w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], co jest niezwykle przydatne w przypadku układu aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie dołączonej właściwości](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Elementy panelu pochodnego  
 Wiele obiektów pochodzi od <xref:System.Windows.Controls.Panel>, ale nie wszystkie z nich są przeznaczone do użycia jako dostawcy układów głównych. Istnieje sześć zdefiniowanych klas paneli (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel> i <xref:System.Windows.Controls.WrapPanel>) zaprojektowanych specjalnie do tworzenia aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Każdy element panelu hermetyzuje własne specjalne funkcje, jak pokazano w poniższej tabeli.  
  
|Nazwa elementu|Panel interfejsu użytkownika?|Opis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Tak|Definiuje obszar, w którym można jawnie pozycjonować elementy podrzędne według współrzędnych względem obszaru <xref:System.Windows.Controls.Canvas>.|  
|<xref:System.Windows.Controls.DockPanel>|Tak|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Tak|Definiuje elastyczny obszar siatki składający się z kolumn i wierszy. Elementy podrzędne <xref:System.Windows.Controls.Grid> można umieścić precyzyjnie przy użyciu właściwości <xref:System.Windows.FrameworkElement.Margin%2A>.|  
|<xref:System.Windows.Controls.StackPanel>|Tak|Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Nie|Obsługuje układ przycisków kart w <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nie|Rozmieszcza zawartość w kontrolce <xref:System.Windows.Controls.ToolBar>.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Nie|<xref:System.Windows.Controls.Primitives.UniformGrid> służy do rozmieszczania elementów podrzędnych w siatce ze wszystkimi równymi rozmiarach komórek.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Nie|Udostępnia klasę bazową dla paneli, które mogą "Wirtualizacja" ich kolekcji podrzędnych.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Tak|Rozmieszcza i wirtualizacji zawartość w jednym wierszu zorientowanym w poziomie lub w pionie.|  
|<xref:System.Windows.Controls.WrapPanel>|Tak|<xref:System.Windows.Controls.WrapPanel> ustawia elementy podrzędne w kolejności sekwencyjnej od lewej do prawej, dzieląc zawartość do następnego wiersza na krawędzi pola zawierającego. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości właściwości <xref:System.Windows.Controls.WrapPanel.Orientation%2A>.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panele interfejsu użytkownika  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostępne są sześć klas, które są zoptymalizowane pod kątem obsługi scenariuszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel> i <xref:System.Windows.Controls.WrapPanel>. Te elementy panelu są łatwe w użyciu, uniwersalne i rozszerzalne dla większości aplikacji.  
  
 Każdy pochodny element <xref:System.Windows.Controls.Panel> traktuje ograniczenia zmiany wielkości inaczej. Zrozumienie, jak <xref:System.Windows.Controls.Panel> obsługuje ograniczenia w poziomie lub w pionie, można bardziej przewidywalnić układ.  
  
|**Nazwa panelu**|**x — wymiar**|**Wymiar y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Ograniczone do zawartości|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.DockPanel>|Ograniczone|Ograniczone|  
|<xref:System.Windows.Controls.StackPanel> (orientacja pionowa)|Ograniczone|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.StackPanel> (Orientacja pozioma)|Ograniczone do zawartości|Ograniczone|  
|<xref:System.Windows.Controls.Grid>|Ograniczone|Ograniczone, z wyjątkiem przypadków, w których <xref:System.Windows.GridUnitType.Auto> stosuje się do wierszy i kolumn|  
|<xref:System.Windows.Controls.WrapPanel>|Ograniczone do zawartości|Ograniczone do zawartości|  
  
 Więcej szczegółowych opisów i przykładów użycia każdego z tych elementów można znaleźć poniżej.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Przestrzeń  
 Element <xref:System.Windows.Controls.Canvas> umożliwia pozycjonowanie zawartości w zależności od absolutnych współrzędnych *x* i *y*. Elementy mogą być rysowane w unikatowej lokalizacji; lub, jeśli elementy zajmują te same współrzędne, kolejność, w której są wyświetlane w znaczniku, określa kolejność, w jakiej są rysowane elementy.  
  
 <xref:System.Windows.Controls.Canvas> to największa elastyczność układu dowolnego <xref:System.Windows.Controls.Panel>. Właściwości Height i Width są używane do definiowania obszaru kanwy, a elementy wewnątrz są przypisane bezwzględnych współrzędnych względem obszaru elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Cztery dołączone właściwości, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, umożliwiają dokładniejszą kontrolę umieszczenia obiektów w <xref:System.Windows.Controls.Canvas>, co pozwala deweloperowi na pozycjonowanie i precyzyjne rozmieszczenie elementów na ekranie.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds na kanwie  
 <xref:System.Windows.Controls.Canvas> może pozycjonować elementy podrzędne w dowolnym miejscu na ekranie, nawet ze współrzędnych, które znajdują się poza własnym zdefiniowanym <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A>. Ponadto rozmiar jego elementów podrzędnych nie ma wpływ na <xref:System.Windows.Controls.Canvas>. W związku z tym, istnieje możliwość, aby element podrzędny mógł narysować inne elementy poza prostokątem granicy elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Domyślne zachowanie <xref:System.Windows.Controls.Canvas> umożliwia narysowanie elementów podrzędnych poza granicami nadrzędnego <xref:System.Windows.Controls.Canvas>. Jeśli to zachowanie jest niepożądane, właściwość <xref:System.Windows.UIElement.ClipToBounds%2A> może być ustawiona na wartość `true`. Powoduje to, że <xref:System.Windows.Controls.Canvas> do przycinania do własnego rozmiaru. <xref:System.Windows.Controls.Canvas> jest jedynym elementem układu, który umożliwia rysowanie elementów podrzędnych poza granicami.  
  
 To zachowanie jest graficznie zilustrowane w [próbce porównania właściwości Width](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definiowanie i używanie kanwy  
 Można utworzyć wystąpienie <xref:System.Windows.Controls.Canvas> po prostu przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu. Poniższy przykład ilustruje sposób użycia <xref:System.Windows.Controls.Canvas> do bezwzględnej pozycji zawartości. Ten kod tworzy 3 100-pikselowe kwadraty. Pierwszy kwadrat jest czerwony, a jego pozycja w lewym górnym rogu (*x, y*) jest określana jako (0, 0). Drugi kwadrat jest zielony, a jego pozycja w lewym górnym rogu wynosi (100, 100), poniżej i z prawej strony pierwszego kwadratu. Trzecia kwadra jest niebieska, a jego pozycja w lewym górnym rogu to (50, 50), co obejmuje dolną i prawą ćwiartkę pierwszego kwadratu i lewy górny Ćwiartka drugiego. Ponieważ trzeci kwadrat jest określany jako ostatni, wygląda na to, że znajduje się on na początku innych dwóch kwadratów — to znaczy, że nakładające się części zakładają kolor trzeciego pola.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które wyglądają następująco.  
  
 ![Typowy element kanwy.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 Element <xref:System.Windows.Controls.DockPanel> używa właściwości dołączonej <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ustawionej w podrzędnych elementach zawartości, aby pozycjonować zawartość wzdłuż krawędzi kontenera. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Controls.Dock.Top> lub <xref:System.Windows.Controls.Dock.Bottom>, ustawia elementy podrzędne powyżej lub poniżej siebie. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Controls.Dock.Left> lub <xref:System.Windows.Controls.Dock.Right>, ustawia elementy podrzędne w lewo lub w prawo. Właściwość <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> określa pozycję końcowego elementu dodanego jako element podrzędny <xref:System.Windows.Controls.DockPanel>.  
  
 Możesz użyć <xref:System.Windows.Controls.DockPanel>, aby ustawić grupę powiązanych kontrolek, takich jak zestaw przycisków. Alternatywnie można go użyć do utworzenia "okienkowego" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobnego do znalezionego w programie Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Ustalanie wielkości do zawartości  
 Jeśli właściwości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> nie są określone, <xref:System.Windows.Controls.DockPanel> rozmiary do zawartości. Rozmiar może zwiększyć lub zmniejszyć do rozmiaru elementów podrzędnych. Jeśli jednak te właściwości są określone i nie jest już miejsce dla następnego określonego elementu podrzędnego, <xref:System.Windows.Controls.DockPanel> nie wyświetla tego elementu podrzędnego ani kolejnych elementów podrzędnych i nie mierzy kolejnych elementów podrzędnych.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> spowoduje "wypełnienie" pozostałego, przydzielonego miejsca. Jeśli to zachowanie nie jest wymagane, ustaw właściwość <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> na `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definiowanie i używanie elementu DockPanel  
 Poniższy przykład ilustruje sposób partycjonowania miejsca przy użyciu <xref:System.Windows.Controls.DockPanel>. Pięć elementów <xref:System.Windows.Controls.Border> jest dodawanych jako elementy podrzędne nadrzędnej <xref:System.Windows.Controls.DockPanel>. Każda z nich używa innej właściwości pozycjonowania <xref:System.Windows.Controls.DockPanel> w celu dzielenia na partycje. Końcowy element "wypełnia" pozostałe, przydzieloną przestrzeń.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które wyglądają następująco.  
  
 ![Typowy scenariusz DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Siatki  
 Element <xref:System.Windows.Controls.Grid> Scala funkcje pozycjonowania bezwzględnego i kontrolki danych tabelarycznych. @No__t-0 umożliwia łatwe pozycjonowanie i Stylowanie elementów. <xref:System.Windows.Controls.Grid> umożliwia zdefiniowanie elastycznych grupowania wierszy i kolumn, a nawet udostępnia mechanizm umożliwiający udostępnianie informacji o rozmiarach między wieloma elementami <xref:System.Windows.Controls.Grid>.  
  
#### <a name="how-is-grid-different-from-table"></a>Czym różni się siatka od tabeli?  
 <xref:System.Windows.Documents.Table> i <xref:System.Windows.Controls.Grid> udostępniają niektóre typowe funkcje, ale każdy z nich jest najlepiej dostosowany do różnych scenariuszy. @No__t-0 jest zaprojektowana do użycia w obrębie zawartości przepływu (zobacz temat [Omówienie dokumentu Flow](../advanced/flow-document-overview.md) , aby uzyskać więcej informacji na temat przepływu zawartości). Siatki najlepiej używać wewnątrz formularzy (zasadniczo poza zawartością przepływu). W <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Table> obsługuje zachowania zawartości przepływu, takie jak stronicowanie, Ponowne wlewanie kolumn i wybór zawartości, podczas gdy <xref:System.Windows.Controls.Grid>. @No__t-0 z drugiej strony najlepiej jest używać poza <xref:System.Windows.Documents.FlowDocument> z wielu powodów, w tym <xref:System.Windows.Controls.Grid> dodaje elementy na podstawie indeksu wierszy i kolumn, <xref:System.Windows.Documents.Table> nie. Element <xref:System.Windows.Controls.Grid> umożliwia warstwową zawartość elementu podrzędnego, co pozwala na istnienie więcej niż jednego elementu w jednej komórce. <xref:System.Windows.Documents.Table> nie obsługuje warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> mogą być absolutnie pozycjonowane względem obszaru ich granic "komórki". <xref:System.Windows.Documents.Table> nie obsługuje tej funkcji. Na koniec wartość <xref:System.Windows.Controls.Grid> jest jaśniejsza niż <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Ustalanie wielkości zachowania kolumn i wierszy  
 Kolumny i wiersze zdefiniowane w <xref:System.Windows.Controls.Grid> mogą korzystać z rozmiarów <xref:System.Windows.GridUnitType.Star>, aby rozłożyć proporcjonalnie do pozostałego miejsca. Gdy wartość <xref:System.Windows.GridUnitType.Star> jest zaznaczona jako wysokość lub szerokość wiersza lub kolumny, ta kolumna lub wiersz otrzymuje ważoną część pozostałego dostępnego miejsca. Jest to w przeciwieństwie do <xref:System.Windows.GridUnitType.Auto>, co spowoduje równomierne rozłożenie przestrzeni na podstawie rozmiaru zawartości w kolumnie lub wierszu. Ta wartość jest wyrażona jako `*` lub `2*` w przypadku używania [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. W pierwszym przypadku wiersz lub kolumna otrzyma jeden raz dostępne miejsce, w drugim przypadku, dwa razy itd. Łącząc tę technikę w celu proporcjonalnego rozłożenia przestrzeni z wartością <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> `Stretch`, istnieje możliwość partycjonowania obszaru układu według wartości procentowej miejsca na ekranie. <xref:System.Windows.Controls.Grid> jest jedynym panelem układu, który może rozproszyć miejsce w ten sposób.  
  
#### <a name="defining-and-using-a-grid"></a>Definiowanie i używanie siatki  
 Poniższy przykład ilustruje sposób tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podobnego do znalezionego w oknie dialogowym uruchamiania dostępnym w menu Start systemu Windows.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które wyglądają następująco.  
  
 ![Typowy element siatki.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 @No__t-0 umożliwia "stos" elementów w przypisanym kierunku. Domyślny kierunek stosu jest pionowy. Właściwość <xref:System.Windows.Controls.StackPanel.Orientation%2A> może służyć do sterowania przepływem zawartości.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel a DockPanel  
 Chociaż <xref:System.Windows.Controls.DockPanel> może również "Stack" elementów podrzędnych, <xref:System.Windows.Controls.DockPanel> i <xref:System.Windows.Controls.StackPanel> nie generują analogicznych wyników w niektórych scenariuszach użycia. Na przykład kolejność elementów podrzędnych może wpływać na ich rozmiar w <xref:System.Windows.Controls.DockPanel>, ale nie w <xref:System.Windows.Controls.StackPanel>. Wynika to z faktu, że <xref:System.Windows.Controls.StackPanel> miar w kierunku układania w <xref:System.Double.PositiveInfinity>, natomiast <xref:System.Windows.Controls.DockPanel> mierzy tylko dostępny rozmiar.  
  
 Poniższy przykład ilustruje tę różnicę klucza.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Różnica w zachowaniu renderowania może być widoczna na tym obrazie.  
  
 ![Zrzut ekranu: StackPanel a DockPanel zrzut ekranu](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definiowanie i używanie elementu StackPanel  
 Poniższy przykład ilustruje sposób użycia <xref:System.Windows.Controls.StackPanel> w celu utworzenia zestawu przycisków umieszczonych w pionie. Dla pozycjonowania poziomego ustaw właściwość <xref:System.Windows.Controls.StackPanel.Orientation%2A> na <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które wyglądają następująco.  
  
 ![Typowy element StackPanel.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również udostępnia odmianę elementu <xref:System.Windows.Controls.StackPanel>, który automatycznie "umożliwia wirtualizację zawartości podrzędnej powiązanej z danymi. W tym kontekście wyraz "Wirtualizacja" odnosi się do techniki, za pomocą której podzbiór elementów jest generowany na podstawie większej liczby elementów danych, w zależności od tego, które elementy są widoczne na ekranie. Jest to czasochłonne, zarówno w zakresie pamięci, jak i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel> (dzięki funkcjom oferowanym przez <xref:System.Windows.Controls.VirtualizingPanel>) oblicza widoczne elementy i współpracuje z <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (na przykład <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ListView>) tylko do tworzenia elementów dla widocznych elementów.  
  
 Element <xref:System.Windows.Controls.VirtualizingStackPanel> jest automatycznie ustawiany jako host elementów dla kontrolek, takich jak <xref:System.Windows.Controls.ListBox>. Podczas hostowania kolekcji powiązanej z danymi zawartość jest automatycznie Zwirtualizowana, o ile zawartość mieści się w granicach <xref:System.Windows.Controls.ScrollViewer>. Znacznie poprawia to wydajność podczas hostowania wielu elementów podrzędnych.  
  
 W poniższym przykładzie pokazano, jak używać <xref:System.Windows.Controls.VirtualizingStackPanel> jako hosta elementów. Aby możliwa była wirtualizacja, właściwość dołączona <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> musi być ustawiona na wartość `true` (domyślnie).  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>Kontrolce WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> służy do pozycjonowania elementów podrzędnych w kolejności sekwencyjnej od lewej do prawej, podczas gdy dociera do krawędzi jego kontenera nadrzędnego. Zawartość może być zorientowana poziomo lub pionowo. <xref:System.Windows.Controls.WrapPanel> jest przydatne w przypadku prostych scenariuszy przepływów [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Może również służyć do zastosowania jednolitego ustalania rozmiarów wszystkich elementów podrzędnych.  
  
 Poniższy przykład ilustruje sposób tworzenia <xref:System.Windows.Controls.WrapPanel>, aby wyświetlić kontrolki <xref:System.Windows.Controls.Button>, które są zawijane, gdy docierają do krawędzi kontenera.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które wyglądają następująco.  
  
 ![Typowy element kontrolce WrapPanel.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Elementy zagnieżdżonych paneli  
 elementy <xref:System.Windows.Controls.Panel> mogą być zagnieżdżane w obrębie siebie w celu utworzenia złożonych układów. Może to okazać się bardzo przydatne w sytuacjach, gdy jeden <xref:System.Windows.Controls.Panel> jest idealny dla części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale może nie spełniać potrzeb różnych części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Nie ma praktycznego limitu liczby zagnieżdżenia, którą aplikacja może obsłużyć, jednak zazwyczaj najlepszym rozwiązaniem jest ograniczenie aplikacji do używania tych paneli, które są niezbędne do odpowiedniego układu. W wielu przypadkach można użyć elementu <xref:System.Windows.Controls.Grid> zamiast zagnieżdżonych paneli ze względu na jego elastyczność jako kontener układu. Może to zwiększyć wydajność aplikacji przez utrzymywanie niepotrzebnych elementów z drzewa.  
  
 Poniższy przykład ilustruje sposób tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], który korzysta z zagnieżdżonych elementów <xref:System.Windows.Controls.Panel> w celu uzyskania określonego układu. W tym konkretnym przypadku element <xref:System.Windows.Controls.DockPanel> jest używany do zapewnienia struktury [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i zagnieżdżonych elementów <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.Canvas> są używane do precyzyjnego pozycjonowania elementów podrzędnych w elemencie nadrzędnym <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], które wyglądają następująco.  
  
 ![Interfejs użytkownika, który korzysta z zagnieżdżonych paneli.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Elementy panelu niestandardowego  
 Mimo że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera tablicę elastycznych kontrolek układu, można również osiągnąć niestandardowe zachowania układu, zastępując metody <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A>. Niestandardowe rozmiary i pozycjonowanie można osiągnąć, definiując nowe zachowania pozycjonowania w ramach tych metod zastąpień.  
  
 Podobnie niestandardowe zachowania układu oparte na klasach pochodnych (takich jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.Grid>) można zdefiniować przez zastępowanie metod <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
 W poniższym przykładzie pokazano, jak utworzyć niestandardowy element <xref:System.Windows.Controls.Panel>. Ten nowy <xref:System.Windows.Controls.Panel>, zdefiniowany jako `PlotPanel`, obsługuje Pozycjonowanie elementów podrzędnych przy użyciu zakodowanych współrzędnych *x* i *y*. W tym przykładzie element <xref:System.Windows.Shapes.Rectangle> (niepokazywany) jest umieszczony w punkcie kreolenia 50 (*x*) i 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Aby wyświetlić bardziej złożoną implementację niestandardowego panelu, zobacz [Tworzenie niestandardowego przykładowego panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Obsługa lokalizacji/globalizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje szereg funkcji, które pomagają w tworzeniu lokalizowalnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Wszystkie elementy panelu natywnie obsługują Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A>, która może być używana do dynamicznego ponownego przepływu zawartości na podstawie ustawień regionalnych lub języka użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Właściwość <xref:System.Windows.Window.SizeToContent%2A> udostępnia mechanizm umożliwiający deweloperom aplikacji przewidywanie potrzeb zlokalizowanych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Użycie wartości <xref:System.Windows.SizeToContent.WidthAndHeight> tej właściwości powoduje, że nadrzędne <xref:System.Windows.Window> są zawsze dynamicznie dopasowane do zawartości i nie są ograniczone przez ograniczenia dotyczące wysokości i szerokości sztucznej.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.StackPanel> są dobranymi opcjami dla lokalizowalnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas> nie jest dobrym wyborem, ponieważ jednak umieszcza zawartość bezwzględnie, co utrudnia lokalizowanie.  
  
 Aby uzyskać dodatkowe informacje na temat tworzenia aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z lokalizowalnymi interfejsami użytkownika (interfejsów użytkownika), zobacz [Omówienie używania automatycznego układu](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Przykład galerii układów WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Wyglądu](../advanced/layout.md)
- [Przykład galerii formantów WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Przegląd wyrównania, marginesów i uzupełniania](../advanced/alignment-margins-and-padding-overview.md)
- [Tworzenie niestandardowego przykładowego panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Przegląd załączonych właściwości](../advanced/attached-properties-overview.md)
- [Korzystanie z automatycznego układu — Omówienie](../advanced/use-automatic-layout-overview.md)
- [Układ i projekt](../advanced/optimizing-performance-layout-and-design.md)
