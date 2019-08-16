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
ms.openlocfilehash: 4f54596e1ce3ed40f3a029ea6703147a97be992f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545271"
---
# <a name="panels-overview"></a>Przegląd Panele
<xref:System.Windows.Controls.Panel>elementy to składniki kontrolujące renderowanie elementów — ich rozmiar i wymiary, ich położenie oraz układ zawartości podrzędnej. Zawiera wiele wstępnie zdefiniowanych <xref:System.Windows.Controls.Panel> elementów, a także możliwość konstruowania elementów niestandardowych <xref:System.Windows.Controls.Panel>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]  
  
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
 <xref:System.Windows.Controls.Panel>jest klasą bazową dla wszystkich elementów, które zapewniają obsługę [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]układu w. Elementy <xref:System.Windows.Controls.Panel> pochodne są używane do pozycjonowania i rozmieszczania [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] elementów w i kodzie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawiera kompleksowy pakiet implementacji panelu pochodnego, które umożliwiają wiele złożonych układów. Te klasy pochodne uwidaczniają właściwości i metody, które pozwalają [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] na większość standardowych scenariuszy. Deweloperzy, którzy nie mogą znaleźć zachowania rozmieszczenia podrzędnego, które spełniają ich potrzeby, mogą tworzyć nowe układy <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> , <xref:System.Windows.FrameworkElement.MeasureOverride%2A> zastępując metody i. Aby uzyskać więcej informacji na temat niestandardowych zachowań układu, zobacz [niestandardowe elementy panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Wspólne elementy członkowskie panelu  
 Wszystkie <xref:System.Windows.Controls.Panel> elementy obsługują podstawowe właściwości ustalania rozmiarów i pozycjonowania <xref:System.Windows.FrameworkElement>zdefiniowane przez <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>w <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>tym <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>,,, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>, i. Aby uzyskać dodatkowe informacje na temat właściwości pozycjonowania zdefiniowanych przez <xref:System.Windows.FrameworkElement>, zobacz [wyrównanie, marginesy i dopełnienie](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>udostępnia dodatkowe właściwości mające krytyczne znaczenie w zrozumieniu i korzystaniu z układu. Właściwość służy do wypełniania obszaru między granicami elementu panelu pochodnego a <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Panel.Children%2A>reprezentuje kolekcję podrzędną elementów, które <xref:System.Windows.Controls.Panel> składa się z. <xref:System.Windows.Controls.Panel.InternalChildren%2A>reprezentuje zawartość <xref:System.Windows.Controls.Panel.Children%2A> kolekcji oraz tych członków wygenerowanych przez powiązanie danych. Oba składają się <xref:System.Windows.Controls.UIElementCollection> z elementów podrzędnych hostowanych w elemencie nadrzędnym <xref:System.Windows.Controls.Panel>.  
  
 Panel udostępnia <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> również przyłączoną właściwość, która może służyć do osiągnięcia kolejności warstwowej w pochodnym <xref:System.Windows.Controls.Panel>. Elementy członkowskie <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu o wyższej <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartości są wyświetlane przed tymi z niższą <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartością. Jest to szczególnie przydatne w przypadku paneli <xref:System.Windows.Controls.Canvas> , <xref:System.Windows.Controls.Grid> takich jak i, które umożliwiają dzieciom udostępnianie tej samej przestrzeni współrzędnych.  
  
 <xref:System.Windows.Controls.Panel>definiuje <xref:System.Windows.Controls.Panel.OnRender%2A> także metodę, która może służyć do przesłonięcia domyślnego zachowania <xref:System.Windows.Controls.Panel>prezentacji.  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Elementy panelu pochodnego sprawiają szerokie użycie dołączonych właściwości. Dołączona właściwość to wyspecjalizowana forma właściwości zależności, która nie ma konwencjonalnej właściwości "otoka" środowiska uruchomieniowego języka wspólnego (CLR). Dołączone właściwości mają wyspecjalizowaną składnię [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]w programie, która może być widoczna w kilku przykładach poniżej.  
  
 Jednym z celów dołączonej właściwości jest umożliwienie elementom podrzędnym przechowywanie unikatowych wartości właściwości, która jest w rzeczywistości zdefiniowana przez element nadrzędny. Zastosowanie tej funkcji ma elementy podrzędne [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], które informują o tym, w jaki sposób mają być prezentowane w, co jest niezwykle przydatne w przypadku układu aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie dołączonej właściwości](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Elementy panelu pochodnego  
 Wiele obiektów pochodzi od <xref:System.Windows.Controls.Panel>, ale nie wszystkie z nich są przeznaczone do użycia jako dostawcy układów głównych. Istnieje sześć zdefiniowanych klas paneli (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>,, i <xref:System.Windows.Controls.WrapPanel>) zaprojektowanych specjalnie na potrzeby tworzenia aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Każdy element panelu hermetyzuje własne specjalne funkcje, jak pokazano w poniższej tabeli.  
  
|Nazwa elementu|Panel interfejsu użytkownika?|Opis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Tak|Definiuje obszar, w obrębie którego możesz jawnie pozycjonować elementy podrzędne według współrzędnych <xref:System.Windows.Controls.Canvas> względem obszaru.|  
|<xref:System.Windows.Controls.DockPanel>|Tak|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Tak|Definiuje elastyczny obszar siatki składający się z kolumn i wierszy. Elementy <xref:System.Windows.Controls.Grid> podrzędne elementu można umieścić precyzyjnie <xref:System.Windows.FrameworkElement.Margin%2A> przy użyciu właściwości.|  
|<xref:System.Windows.Controls.StackPanel>|Tak|Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Nie|Obsługuje układ przycisków karty w <xref:System.Windows.Controls.TabControl>elemencie.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nie|Rozmieszcza zawartość w <xref:System.Windows.Controls.ToolBar> formancie.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Nie|<xref:System.Windows.Controls.Primitives.UniformGrid>służy do rozmieszczania elementów podrzędnych w siatce ze wszystkimi równymi rozmiarach komórek.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Nie|Udostępnia klasę bazową dla paneli, które mogą "Wirtualizacja" ich kolekcji podrzędnych.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Tak|Rozmieszcza i wirtualizacji zawartość w jednym wierszu zorientowanym w poziomie lub w pionie.|  
|<xref:System.Windows.Controls.WrapPanel>|Tak|<xref:System.Windows.Controls.WrapPanel>położenie elementów podrzędnych w kolejności od lewej do prawej, przerwanie zawartości do następnego wiersza na krawędzi pola zawierającego. Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panele interfejsu użytkownika  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] W programie są dostępne sześć klas paneli, które są zoptymalizowane pod kątem <xref:System.Windows.Controls.DockPanel>obsługi <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy: <xref:System.Windows.Controls.Canvas>,, <xref:System.Windows.Controls.WrapPanel>,, i. Te elementy panelu są łatwe w użyciu, uniwersalne i rozszerzalne dla większości aplikacji.  
  
 Każdy element <xref:System.Windows.Controls.Panel> pochodny traktuje ograniczenia zmiany wielkości inaczej. Zrozumienie, jak <xref:System.Windows.Controls.Panel> ograniczenia w poziomie lub w pionie mogą sprawiać przewidywalność układu.  
  
|**Nazwa panelu**|**x-Dimension**|**Wymiar y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Ograniczone do zawartości|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.DockPanel>|Ograniczone|Ograniczone|  
|<xref:System.Windows.Controls.StackPanel>(Orientacja pionowa)|Ograniczone|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.StackPanel>(Orientacja pozioma)|Ograniczone do zawartości|Ograniczone|  
|<xref:System.Windows.Controls.Grid>|Ograniczone|Ograniczone, z wyjątkiem przypadków, gdy <xref:System.Windows.GridUnitType.Auto> mają zastosowanie do wierszy i kolumn|  
|<xref:System.Windows.Controls.WrapPanel>|Ograniczone do zawartości|Ograniczone do zawartości|  
  
 Więcej szczegółowych opisów i przykładów użycia każdego z tych elementów można znaleźć poniżej.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Kanwa  
 Element umożliwia pozycjonowanie zawartości według absolutnych współrzędnych x i *y*. <xref:System.Windows.Controls.Canvas> Elementy mogą być rysowane w unikatowej lokalizacji; lub, jeśli elementy zajmują te same współrzędne, kolejność, w której są wyświetlane w znaczniku, określa kolejność, w jakiej są rysowane elementy.  
  
 <xref:System.Windows.Controls.Canvas>zapewnia najbardziej elastyczną obsługę <xref:System.Windows.Controls.Panel>układu. Właściwości Height i Width są używane do definiowania obszaru kanwy, a elementy wewnątrz są przypisane bezwzględnych współrzędnych względem obszaru elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Cztery dołączone właściwości, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas>, i ,<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>umożliwiają dokładniejszą kontrolę nad umieszczaniem obiektów w obrębie, co umożliwia deweloperom pozycjonowanie i precyzyjne porządkowanie elementów na ekranie. <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType>  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds na kanwie  
 <xref:System.Windows.Controls.Canvas>można umieścić elementy podrzędne w dowolnym miejscu na ekranie, nawet ze współrzędnymi, które są poza własnym <xref:System.Windows.FrameworkElement.Height%2A> zdefiniowanym <xref:System.Windows.FrameworkElement.Width%2A>i. Ponadto nie <xref:System.Windows.Controls.Canvas> ma to wpływ na rozmiar jego elementów podrzędnych. W związku z tym jest możliwe, aby element podrzędny mógł narysować inne elementy poza prostokątem granicy elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Domyślnym zachowaniem <xref:System.Windows.Controls.Canvas> jest zezwolenie na narysowanie elementów podrzędnych poza granicami elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Jeśli to zachowanie jest niepożądane, <xref:System.Windows.UIElement.ClipToBounds%2A> Właściwość można ustawić na. `true` Przyczyną <xref:System.Windows.Controls.Canvas> tego jest przycinanie do własnego rozmiaru. <xref:System.Windows.Controls.Canvas>jest jedynym elementem układu, który umożliwia rysowanie elementów podrzędnych poza granicami.  
  
 To zachowanie jest graficznie zilustrowane w próbce [porównania właściwości Width](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definiowanie i używanie kanwy  
 Można utworzyć wystąpienie po prostu przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu lub. <xref:System.Windows.Controls.Canvas> W poniższym przykładzie pokazano, jak za <xref:System.Windows.Controls.Canvas> pomocą do bezwzględnie pozycjonować zawartość. Ten kod tworzy 3 100-pikselowe kwadraty. Pierwszy kwadrat jest czerwony, a jego pozycja w lewym górnym rogu (*x, y*) jest określana jako (0, 0). Drugi kwadrat jest zielony, a jego pozycja w lewym górnym rogu wynosi (100, 100), poniżej i z prawej strony pierwszego kwadratu. Trzecia kwadra jest niebieska, a jego pozycja w lewym górnym rogu to (50, 50), co obejmuje dolną i prawą ćwiartkę pierwszego kwadratu i lewy górny Ćwiartka drugiego. Ponieważ trzeci kwadrat jest określany jako ostatni, wygląda na to, że znajduje się on na początku innych dwóch kwadratów — to znaczy, że nakładające się części zakładają kolor trzeciego pola.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , które wygląda następująco.  
  
 ![Typowy element kanwy.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Element<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> używa dołączonej właściwości zgodnie z ustawieniem w podrzędnych elementach zawartości, aby pozycjonować zawartość wzdłuż krawędzi kontenera. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Controls.Dock.Top> lub <xref:System.Windows.Controls.Dock.Bottom>, ustawia elementy podrzędne powyżej lub poniżej siebie. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Controls.Dock.Left> lub <xref:System.Windows.Controls.Dock.Right>, ustawia elementy podrzędne w lewo lub w prawo. Właściwość określa pozycję końcowego elementu dodanego jako element podrzędny <xref:System.Windows.Controls.DockPanel>elementu. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>  
  
 Można użyć <xref:System.Windows.Controls.DockPanel> , aby pomieścić grupę powiązanych kontrolek, takich jak zestaw przycisków. Alternatywnie można użyć go do utworzenia "okienkowego" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobnego do znalezionego w programie Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Ustalanie wielkości do zawartości  
 Jeśli jego <xref:System.Windows.FrameworkElement.Height%2A> właściwości <xref:System.Windows.FrameworkElement.Width%2A> i nie są określone, <xref:System.Windows.Controls.DockPanel> rozmiary do zawartości. Rozmiar może zwiększyć lub zmniejszyć do rozmiaru elementów podrzędnych. Jednak jeśli te właściwości są określone i nie jest już miejsce dla następnego określonego elementu podrzędnego, program <xref:System.Windows.Controls.DockPanel> nie wyświetla tego elementu podrzędnego ani kolejnych elementów podrzędnych i nie mierzy kolejnych elementów podrzędnych.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Domyślnie ostatni element podrzędny <xref:System.Windows.Controls.DockPanel> elementu będzie wypełniać pozostałe, przydzielone miejsce. Jeśli to zachowanie nie jest wymagane, ustaw <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> właściwość na `false`wartość.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definiowanie i używanie elementu DockPanel  
 Poniższy przykład ilustruje sposób partycjonowania miejsca przy użyciu <xref:System.Windows.Controls.DockPanel>. Pięć <xref:System.Windows.Controls.Border> elementów jest dodawanych jako elementy podrzędne elementu <xref:System.Windows.Controls.DockPanel>nadrzędnego. Każda z nich używa innej właściwości <xref:System.Windows.Controls.DockPanel> pozycjonowania do obszaru partycji. Końcowy element "wypełnia" pozostałe, przydzieloną przestrzeń.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , które wygląda następująco.  
  
 ![Typowy scenariusz DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Siatka  
 <xref:System.Windows.Controls.Grid> Element Scala funkcje pozycjonowania bezwzględnego i kontrolki danych tabelarycznych. A <xref:System.Windows.Controls.Grid> umożliwia łatwe pozycjonowanie elementów i stylów. <xref:System.Windows.Controls.Grid>umożliwia zdefiniowanie elastycznych grupowania wierszy i kolumn, a nawet udostępnia mechanizm umożliwiający udostępnianie informacji o rozmiarach między wieloma <xref:System.Windows.Controls.Grid> elementami.  
  
#### <a name="how-is-grid-different-from-table"></a>Czym różni się siatka od tabeli?  
 <xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> udostępniaj niektóre typowe funkcje, ale każdy z nich jest najlepiej dostosowany do różnych scenariuszy. Jest <xref:System.Windows.Documents.Table> przeznaczony do użycia w obrębie zawartości przepływu (zobacz temat [Omówienie dokumentu Flow](../advanced/flow-document-overview.md) , aby uzyskać więcej informacji na temat przepływu zawartości). Siatki najlepiej używać wewnątrz formularzy (zasadniczo poza zawartością przepływu). W programie obsługuje zachowania zawartości przepływu, takie jak stronicowanie, Ponowne wlewanie kolumn <xref:System.Windows.Controls.Grid> i wybór zawartości, a nie. <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.FlowDocument> Z drugiej strony najlepiej używać poza a <xref:System.Windows.Documents.FlowDocument> z wielu powodów, takich jak <xref:System.Windows.Controls.Grid> Dodawanie elementów opartych na indeksie wierszy i kolumn, <xref:System.Windows.Documents.Table> nie. <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid> Element umożliwia warstwową zawartość elementu podrzędnego, co pozwala na istnienie więcej niż jednego elementu w jednej komórce. <xref:System.Windows.Documents.Table>nie obsługuje warstw. Elementy podrzędne elementu <xref:System.Windows.Controls.Grid> mogą być absolutnie pozycjonowane względem obszaru ich granic "komórki". <xref:System.Windows.Documents.Table>Program nie obsługuje tej funkcji. Na <xref:System.Windows.Controls.Grid> koniec jest to jaśniejsza waga <xref:System.Windows.Documents.Table>od.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Ustalanie wielkości zachowania kolumn i wierszy  
 Kolumny i wiersze zdefiniowane w ramach <xref:System.Windows.Controls.Grid> programu mogą korzystać z <xref:System.Windows.GridUnitType.Star> wielkości, aby w celu rozdzielenia pozostałego miejsca. Gdy <xref:System.Windows.GridUnitType.Star> jest wybrana jako wysokość lub szerokość wiersza lub kolumny, ta kolumna lub wiersz otrzymuje ważoną część pozostałego dostępnego miejsca. Jest to w przeciwieństwie <xref:System.Windows.GridUnitType.Auto>do, co spowoduje równomierne rozłożenie przestrzeni na podstawie rozmiaru zawartości w kolumnie lub wierszu. Ta wartość jest wyrażona `*` jako `2*` lub podczas [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]korzystania z. W pierwszym przypadku wiersz lub kolumna otrzyma jeden raz dostępne miejsce, w drugim przypadku, dwa razy itd. Łącząc tę technikę w celu proporcjonalnego rozproszenia miejsca <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> przy <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> użyciu wartości `Stretch` i, można podzielić na partycje obszar układu według wartości procentowej miejsca na ekranie. <xref:System.Windows.Controls.Grid>jest jedynym panelem układu, który może rozproszyć miejsce w ten sposób.  
  
#### <a name="defining-and-using-a-grid"></a>Definiowanie i używanie siatki  
 Poniższy przykład ilustruje, jak utworzyć [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podobny do, który znajduje się w oknie dialogowym uruchamiania dostępnym [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] w menu Start.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , które wygląda następująco.  
  
 ![Typowy element siatki.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umożliwia "stos" elementów w przypisanym kierunku. Domyślny kierunek stosu jest pionowy. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Właściwość może służyć do sterowania przepływem zawartości.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel a DockPanel  
 Chociaż <xref:System.Windows.Controls.DockPanel> mogą również "Stack" <xref:System.Windows.Controls.DockPanel> elementy podrzędne i <xref:System.Windows.Controls.StackPanel> nie generować analogicznych wyników w niektórych scenariuszach użycia. Na przykład kolejność elementów podrzędnych może wpływać na ich rozmiar w, <xref:System.Windows.Controls.DockPanel> ale nie <xref:System.Windows.Controls.StackPanel>w. Wynika to z <xref:System.Windows.Controls.StackPanel> faktu <xref:System.Double.PositiveInfinity>, że miary w kierunku układania w, <xref:System.Windows.Controls.DockPanel> podczas gdy mierzy tylko dostępny rozmiar.  
  
 Poniższy przykład ilustruje tę różnicę klucza.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Różnica w zachowaniu renderowania może być widoczna na tym obrazie.  
  
 ![Zrzut ekranu StackPanel a DockPanel zrzut]ekranu(./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definiowanie i używanie elementu StackPanel  
 W poniższym przykładzie pokazano, jak za pomocą <xref:System.Windows.Controls.StackPanel> programu utworzyć zestaw przycisków umieszczonych w pionie. Dla pozycjonowania poziomego Ustaw <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwość na <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , które wygląda następująco.  
  
 ![Typowy element StackPanel.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera również odmianę <xref:System.Windows.Controls.StackPanel> elementu, który automatycznie "umożliwia wirtualizację zawartości podrzędnej powiązanej z danymi. W tym kontekście wyraz "Wirtualizacja" odnosi się do techniki, za pomocą której podzbiór elementów jest generowany na podstawie większej liczby elementów danych, w zależności od tego, które elementy są widoczne na ekranie. Jest to czasochłonne, zarówno w zakresie pamięci, jak i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel>(za pośrednictwem funkcji <xref:System.Windows.Controls.VirtualizingPanel>zapewnianych przez program) oblicza widoczne elementy <xref:System.Windows.Controls.ItemContainerGenerator> i współpracuje <xref:System.Windows.Controls.ItemsControl> z obiektem <xref:System.Windows.Controls.ListBox> od <xref:System.Windows.Controls.ListView>a (na przykład lub) do tworzenia tylko elementów dla widocznych elementów.  
  
 Element jest automatycznie ustawiany jako host elementów dla kontrolek, takich <xref:System.Windows.Controls.ListBox>jak. <xref:System.Windows.Controls.VirtualizingStackPanel> Podczas hostowania kolekcji powiązanej z danymi zawartość jest automatycznie Zwirtualizowana, o ile zawartość znajduje się w granicach <xref:System.Windows.Controls.ScrollViewer>. Znacznie poprawia to wydajność podczas hostowania wielu elementów podrzędnych.  
  
 W poniższym przykładzie pokazano, jak używać <xref:System.Windows.Controls.VirtualizingStackPanel> jako hosta elementów. Dołączona właściwość musi być ustawiona na `true` wartość (domyślnie), aby można było przeprowadzić wirtualizację. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>służy do pozycjonowania elementów podrzędnych w kolejności sekwencyjnej od lewej do prawej, przerwanie zawartości do następnego wiersza, gdy dociera do krawędzi jego kontenera nadrzędnego. Zawartość może być zorientowana poziomo lub pionowo. <xref:System.Windows.Controls.WrapPanel>jest przydatne w przypadku prostych [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy przepływu. Może również służyć do zastosowania jednolitego ustalania rozmiarów wszystkich elementów podrzędnych.  
  
 Poniższy przykład ilustruje sposób tworzenia <xref:System.Windows.Controls.WrapPanel> do wyświetlania <xref:System.Windows.Controls.Button> formantów, które są zawijane, gdy docierają do krawędzi kontenera.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , które wygląda następująco.  
  
 ![Typowy element kontrolce WrapPanel.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Elementy zagnieżdżonych paneli  
 <xref:System.Windows.Controls.Panel>elementy mogą być zagnieżdżane w obrębie siebie w celu utworzenia złożonych układów. Może to okazać się bardzo przydatne w sytuacjach <xref:System.Windows.Controls.Panel> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], gdy jeden z nich jest idealny dla części, ale może nie spełniać potrzeb różnych fragmentów [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Nie ma praktycznego limitu liczby zagnieżdżenia, którą aplikacja może obsłużyć, jednak zazwyczaj najlepszym rozwiązaniem jest ograniczenie aplikacji do używania tych paneli, które są niezbędne do odpowiedniego układu. W wielu przypadkach <xref:System.Windows.Controls.Grid> można użyć elementu zamiast zagnieżdżonych paneli ze względu na jego elastyczność jako kontener układu. Może to zwiększyć wydajność aplikacji przez utrzymywanie niepotrzebnych elementów z drzewa.  
  
 W poniższym przykładzie pokazano, jak utworzyć element [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , który korzysta z elementów <xref:System.Windows.Controls.Panel> zagnieżdżonych w celu osiągnięcia określonego układu. <xref:System.Windows.Controls.DockPanel> W tym konkretnym przypadku element jest używany do zapewnienia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] struktury, <xref:System.Windows.Controls.Grid>a elementy zagnieżdżone <xref:System.Windows.Controls.StackPanel> , a i a <xref:System.Windows.Controls.Canvas> są używane do precyzyjnego pozycjonowania elementów podrzędnych w elemencie nadrzędnym <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Skompilowana aplikacja daje nowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , które wygląda następująco.  
  
 ![Interfejs użytkownika, który korzysta z zagnieżdżonych paneli.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Elementy panelu niestandardowego  
 Chociaż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje tablicę elastycznych kontrolek układu, niestandardowe zachowania układu można również osiągnąć przez <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> zastąpienie metod i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> . Niestandardowe rozmiary i pozycjonowanie można osiągnąć, definiując nowe zachowania pozycjonowania w ramach tych metod zastąpień.  
  
 Podobnie niestandardowe zachowania układu oparte na klasach pochodnych (takich jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.Grid>) można definiować poprzez zastępowanie ich <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod <xref:System.Windows.FrameworkElement.MeasureOverride%2A> i.  
  
 Poniższy znacznik ilustruje sposób tworzenia niestandardowego <xref:System.Windows.Controls.Panel> elementu. Ten nowy <xref:System.Windows.Controls.Panel>, zdefiniowany jako `PlotPanel`, obsługuje Pozycjonowanie elementów podrzędnych za pomocą zakodowanych przez siebie współrzędnych *x* i *y*. W tym przykładzie <xref:System.Windows.Shapes.Rectangle> element (niepokazywany) jest umieszczony w punkcie kreolenia 50 (*x*) i 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Aby wyświetlić bardziej złożoną implementację niestandardowego panelu, zobacz [Tworzenie niestandardowego przykładowego panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Obsługa lokalizacji/globalizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Program obsługuje szereg funkcji, które pomagają w tworzeniu lokalizowalnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Wszystkie elementy panelu natywnie obsługują <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość, która może być używana do dynamicznego ponownego przepływu zawartości na podstawie ustawień regionalnych lub języka użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Właściwość zawiera mechanizm, który umożliwia deweloperom aplikacji przewidywanie potrzeb zlokalizowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Window.SizeToContent%2A> Korzystając z <xref:System.Windows.Window> wartości tej właściwości, element nadrzędny zawsze ma rozmiary dynamiczne w celu dopasowania do zawartości i nie jest ograniczony przez ograniczenia dotyczące wysokości i szerokości. <xref:System.Windows.SizeToContent.WidthAndHeight>  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, i <xref:System.Windows.Controls.StackPanel> są dobranymi opcjami dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]lokalizowalności. <xref:System.Windows.Controls.Canvas>nie jest dobrym wyborem, ponieważ jednak umieszcza zawartość bezwzględnie, co utrudnia lokalizowanie.  
  
 Aby uzyskać dodatkowe informacje na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temat tworzenia aplikacji [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]z lokalizowalnymi, zobacz [Omówienie używania automatycznego układu](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Przykład galerii układów WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Układ](../advanced/layout.md)
- [Przykład galerii formantów WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Przegląd wyrównania, marginesów i wypełnień](../advanced/alignment-margins-and-padding-overview.md)
- [Tworzenie niestandardowego przykładowego panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md)
- [Przegląd używania automatycznego układu](../advanced/use-automatic-layout-overview.md)
- [Układ i projekt](../advanced/optimizing-performance-layout-and-design.md)
