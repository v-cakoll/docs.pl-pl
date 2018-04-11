---
title: Przegląd Panele
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
caps.latest.revision: 48
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd04413636c7d6182ff01712eecedbbd4ed02761
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="panels-overview"></a>Przegląd Panele
<xref:System.Windows.Controls.Panel> elementy są składniki, które kontrolują renderowanie elementów — ich rozmiar i wymiarów, ich pozycji i rozmieszczenia ich zawartość elementu podrzędnego. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Zawiera szereg wstępnie zdefiniowanych <xref:System.Windows.Controls.Panel> elementy, a także możliwość tworzenia niestandardowych <xref:System.Windows.Controls.Panel> elementów.  
  
 Ten temat zawiera następujące sekcje.  
  
-   [Klasa panelu](#Panels_view_from_10000_feet)  
  
-   [Wspólne elementy członkowskie panel elementu](#Panels_declared_members)  
  
-   [Elementy pochodne panelu](#Panels_derived_elements)  
  
-   [Panele interfejsu użytkownika](#Panels_main_UI_elements)  
  
-   [Elementy panelu zagnieżdżonych](#Panels_nested_panel_elements)  
  
-   [Elementy panelu niestandardowych](#Panels_custom_panel_elements)  
  
-   [Obsługa lokalizacji/globalizacji](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Klasa panelu  
 <xref:System.Windows.Controls.Panel> jest klasą bazową dla wszystkich elementów, które zapewniają układu obsługuje w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Pochodnych <xref:System.Windows.Controls.Panel> elementy są używane do pozycjonowania i rozmieszczania elementów w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zawiera kompleksowe pakiet implementacji pochodnej panelu, które umożliwiają wielu złożonych układów. Te klasy pochodnej ujawnić właściwości i metod umożliwiających większości standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy. Deweloperzy, którzy nie mogą odnaleźć zachowanie rozmieszczenie podrzędne, które spełnia ich potrzeb można tworzyć nowe układy przez zastąpienie <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Aby uzyskać więcej informacji dotyczących zachowania niestandardowego układu, zobacz [niestandardowe elementy panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Typowe członków zespołu  
 Wszystkie <xref:System.Windows.Controls.Panel> elementy obsługują base zmiany rozmiaru i pozycjonowania właściwości zdefiniowane przez <xref:System.Windows.FrameworkElement>, takie jak <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, i <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Dodatkowe informacje na temat właściwości zdefiniowane przez pozycjonowania <xref:System.Windows.FrameworkElement>, zobacz [wyrównanie, marginesy i dopełnienia omówienie](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> udostępnia dodatkowe właściwości, które są krytyczne znaczenie w opisu i użytkowania układu. <xref:System.Windows.Controls.Panel.Background%2A> Właściwość jest używana, aby wypełnił obszar między granice elementu panel pochodnych z <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A> reprezentuje kolekcję elementów podrzędnych który <xref:System.Windows.Controls.Panel> składa się z. <xref:System.Windows.Controls.Panel.InternalChildren%2A> reprezentuje zawartość <xref:System.Windows.Controls.Panel.Children%2A> kolekcji oraz tych członków, generowane przez powiązanie danych. Oba składają się z <xref:System.Windows.Controls.UIElementCollection> elementów podrzędnych hostowanej nadrzędnym <xref:System.Windows.Controls.Panel>.  
  
 Panel również ujawnia <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> dołączona właściwość, który może służyć do osiągnięcia warstwowego kolejności w pochodnym <xref:System.Windows.Controls.Panel>. Członkowie zespołu <xref:System.Windows.Controls.Panel.Children%2A> kolekcji o wyższej <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartości są wyświetlane przed elementami z niższej <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartość. Jest to szczególnie przydatne dla paneli takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.Grid> które zezwalają na elementy podrzędne na współużytkowanie tej samej przestrzeni współrzędnych.  
  
 <xref:System.Windows.Controls.Panel> definiuje również <xref:System.Windows.Controls.Panel.OnRender%2A> metodę, która umożliwia zastąpienie zachowania domyślnego prezentacji z <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Pochodne tych elementów należy zwiększone użycie dołączone właściwości. Dołączona właściwość jest specjalna forma właściwości zależności, który nie ma umownego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości "otoki". Dołączone właściwości mają specjalne składni w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], które są widoczne w kilku przykłady, które należy wykonać.  
  
 Jeden cel dołączona właściwość jest umożliwienie podrzędne elementy do przechowywania unikatowe wartości właściwości, która faktycznie jest definiowana za pomocą elementu nadrzędnego. Aplikacja ta funkcja ma elementy podrzędne, które informują nadrzędnego, jak ma być przedstawiane w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], który jest bardzo przydatne w przypadku układu aplikacji. Aby uzyskać więcej informacji, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Elementy pochodne panelu  
 Wiele obiektów pochodzi od <xref:System.Windows.Controls.Panel>, ale nie wszystkie z nich są przeznaczone do użytku jako głównego układu dostawcy. Brak sześciu klas zdefiniowanych panelu (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, i <xref:System.Windows.Controls.WrapPanel>) te zostały zaprojektowane specjalnie z myślą o tworzeniu aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Każdy element Panelu hermetyzuje własną specjalne funkcje, jak pokazano w poniższej tabeli.  
  
|Nazwa elementu|Panel interfejsu użytkownika?|Opis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Tak|Definiuje obszar, w którym możesz jawnie pozycjonować elementy podrzędne współrzędnymi względem <xref:System.Windows.Controls.Canvas> obszaru.|  
|<xref:System.Windows.Controls.DockPanel>|Tak|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub pionie względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Tak|Definiuje elastyczny obszar siatki składające się z kolumnami i wierszami. Elementy podrzędne <xref:System.Windows.Controls.Grid> może być umieszczony dokładnie przy użyciu <xref:System.Windows.FrameworkElement.Margin%2A> właściwości.|  
|<xref:System.Windows.Controls.StackPanel>|Tak|Rozmieszcza elementy potomne w jednym wierszu, które mogą być rozmieszczane poziomo czy pionowo.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Nie|Obsługuje układ przycisków karty w <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nie|Rozmieszcza zawartość w <xref:System.Windows.Controls.ToolBar> formantu.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Nie|<xref:System.Windows.Controls.Primitives.UniformGrid> Służy do rozmieszczania elementów podrzędnych w siatce o różnej wielkości komórki takie same.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Nie|Udostępnia klasę podstawową dla panele, które "zwirtualizować" ich kolekcji elementów podrzędnych.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Tak|Rozmieszcza i Wirtualizuje zawartość pojedynczej linii ukierunkowane poziomo czy pionowo.|  
|<xref:System.Windows.Controls.WrapPanel>|Tak|<xref:System.Windows.Controls.WrapPanel> Ustawia elementy podrzędne sekwencyjnie od lewej do prawej, dzielenia zawartości do następnego wiersza na krawędzi zawierającego pola. Następne uporządkowanie zachodzi sekwencyjnie od góry do dołu lub od prawej do lewej w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panele interfejsu użytkownika  
 Są dostępne w sześciu klas panelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] który są zoptymalizowane pod kątem obsługi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariusze: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, i <xref:System.Windows.Controls.WrapPanel>. Te elementy panelu są łatwe w użyciu, elastyczne i rozszerzalny dla większości aplikacji.  
  
 Każdy pochodnych <xref:System.Windows.Controls.Panel> element traktuje ograniczenia rozmiaru inaczej. Opis sposobu <xref:System.Windows.Controls.Panel> ograniczenia dojść w poziomie lub pionie kierunku ułatwia układu bardziej przewidywalne.  
  
|**Nazwa panelu**|**x-Dimension**|**Wymiar y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Ograniczone do zawartości|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.DockPanel>|Ograniczone|Ograniczone|  
|<xref:System.Windows.Controls.StackPanel> (Orientacji pionowej)|Ograniczone|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.StackPanel> (Orientacja pozioma)|Ograniczone do zawartości|Ograniczone|  
|<xref:System.Windows.Controls.Grid>|Ograniczone|Ograniczone, z wyjątkiem przypadków, gdy <xref:System.Windows.GridUnitType.Auto> dotyczą wierszy i kolumn|  
|<xref:System.Windows.Controls.WrapPanel>|Ograniczone do zawartości|Ograniczone do zawartości|  
  
 Poniżej znajdują się szczegółowe opisy i przykłady użycia każdego z tych elementów.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Kanwa  
 <xref:System.Windows.Controls.Canvas> Element włącza rozmieszczania zawartości zgodnie z bezwzględną *x -* i *y -*współrzędnych. Elementy mogą znajdować się na środku unikatową lokalizację; lub, jeśli elementy zajmują te same współrzędne, kolejność znacznika określa kolejność, w którym są rysowane elementów.  
  
 <xref:System.Windows.Controls.Canvas> najbardziej elastycznym obsługuje układ dowolnego <xref:System.Windows.Controls.Panel>. Właściwości wysokość i szerokość są używane do definiowania obszarze roboczym i elementy wewnątrz przypisanych współrzędne bezwzględne względem obszaru macierzystego <xref:System.Windows.Controls.Canvas>. Cztery dołączone właściwości, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, Zezwalaj precyzyjnego położenie obiektu <xref:System.Windows.Controls.Canvas>, dzięki czemu Deweloper to pozycjonowania i rozmieszczania elementów dokładnie na ekranie.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Element ClipToBounds wewnątrz obszaru roboczego  
 <xref:System.Windows.Controls.Canvas> można pozycjonować elementy podrzędne w dowolnym miejscu na ekranie, nawet na współrzędne, które znajdują się poza własne zdefiniowane <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A>. Ponadto <xref:System.Windows.Controls.Canvas> nie ma wpływu na rozmiar z jej ról podrzędnych. W związku z tym jest możliwe w dla elementu podrzędnego do innych elementów poza prostokątem nadrzędnego overdraw <xref:System.Windows.Controls.Canvas>. Domyślne zachowanie <xref:System.Windows.Controls.Canvas> jest umożliwienie dzieci być rysowane poza granicami obiektu nadrzędnego <xref:System.Windows.Controls.Canvas>. Jeśli to zachowanie jest niepożądane, <xref:System.Windows.UIElement.ClipToBounds%2A> ustawioną właściwość `true`. Powoduje to <xref:System.Windows.Controls.Canvas> do klipu do jego własnej rozmiaru. <xref:System.Windows.Controls.Canvas> jest to element układu tylko umożliwiający dzieci być rysowane poza jej zakresem.  
  
 To zachowanie graficznie przedstawia [przykład porównania właściwości szerokość](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definiowanie i przy użyciu obszaru roboczego  
 A <xref:System.Windows.Controls.Canvas> można wdrożyć przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu. W poniższym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.Canvas> absolutnie położenie zawartości. Ten kod tworzy trzy pola 100 pikseli. Pierwszy kwadrat jest czerwony i jego lewego górnego (*x, y*) pozycja jest określona jako (0, 0). Drugi kwadratowe jest zielony, a jego położenie lewego górnego (100, 100), poniżej i po prawej stronie pierwszy kwadratowe. Trzeci kwadrat jest niebieski, a jego położenie lewego górnego (50, 50), w związku z tym obejmujące wiązania kwadrantu prawym dolnym pierwszy kwadratu i wiązania kwadrantu lewej górnej drugiego. Ponieważ trzeci kwadrat jest rozmieszczona ostatnich, prawdopodobnie jest on na dwa pola — to znaczy nakładające się części założono, kolor trzecim polu.  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja zwraca nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wygląda jak to.  
  
 ![Typowy Element Canvas. ] (../../../../docs/framework/wpf/controls/media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Element używa <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączona właściwość zgodnie z ustawieniami w zawartości elementów podrzędnych, aby umieścić zawartość wzdłuż krawędzi kontenera. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ustawiono <xref:System.Windows.Controls.Dock.Top> lub <xref:System.Windows.Controls.Dock.Bottom>, umieszcza jego elementy podrzędne powyżej lub poniżej siebie nawzajem. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ustawiono <xref:System.Windows.Controls.Dock.Left> lub <xref:System.Windows.Controls.Dock.Right>, umieszcza jego elementy podrzędne w lewo lub w prawo do siebie. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> Właściwość określa położenie elementu końcowego dodany jako element podrzędny <xref:System.Windows.Controls.DockPanel>.  
  
 Można użyć <xref:System.Windows.Controls.DockPanel> umieścić grupy powiązanych formantów, takich jak zestaw przycisków. Alternatywnie można ją utworzyć w "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobnie jak w [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>Ustawianie rozmiaru zawartości  
 Jeśli jej <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości nie są określone, <xref:System.Windows.Controls.DockPanel> rozmiary, do jego zawartości. Rozmiar można zwiększyć lub zmniejszyć aby zmieścił się jego elementów podrzędnych. Jednak jeśli te właściwości są określone i nie ma miejsca na następny element podrzędny określonego <xref:System.Windows.Controls.DockPanel> nie wyświetla tego elementu podrzędnego lub elementy kolejne podrzędne i nie pomiaru elementy podrzędne kolejne.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> elementu "wypełni" pozostałą, nieprzydzielone miejsce. Jeśli to zachowanie jest niepożądane, ustaw <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> właściwości `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definiowanie i przy użyciu elementu DockPanel  
 W poniższym przykładzie pokazano sposób partycji przy użyciu miejsca <xref:System.Windows.Controls.DockPanel>. Pięć <xref:System.Windows.Controls.Border> elementy są dodawane jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>. Każda z nich używa innego Właściwość pozycjonowania <xref:System.Windows.Controls.DockPanel> przestrzeń partycji. Końcowy element "wypełnia" pozostała, nieprzydzielone miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja zwraca nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wygląda jak to.  
  
 ![Typowy scenariusz DockPanel. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Siatka  
 <xref:System.Windows.Controls.Grid> Element scala funkcji bezwzględny i kontroli danych tabelarycznych. A <xref:System.Windows.Controls.Grid> umożliwia łatwe pozycji i styl elementów. <xref:System.Windows.Controls.Grid> można zdefiniować elastyczne wierszy i kolumn grupowania, a nawet zapewnia mechanizm udostępnianie informacji zmiany rozmiaru między wieloma <xref:System.Windows.Controls.Grid> elementów.  
  
#### <a name="how-is-grid-different-from-table"></a>Czym różni się siatki z tabeli?  
 <xref:System.Windows.Documents.Table> i <xref:System.Windows.Controls.Grid> udostępnianie niektóre typowe funkcje, ale każda jest najbardziej odpowiednie dla różnych scenariuszy. A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w dowolnej zawartości (zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md) uzyskać więcej informacji o dowolnej zawartości). Najlepiej sprawdzają siatki wewnątrz formularzy (zasadniczo dowolnym poza przepływ zawartości). W ramach <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> obsługuje przepływ zachowania zawartości, takie jak podział na strony, ze zmianą ułożenia kolumn i wybór zawartości podczas <xref:System.Windows.Controls.Grid> nie. A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej jest używana poza <xref:System.Windows.Documents.FlowDocument> wielu powodów, takich jak <xref:System.Windows.Controls.Grid> dodaje elementy oparte na indeks wierszy i kolumn <xref:System.Windows.Documents.Table> nie. <xref:System.Windows.Controls.Grid> Element umożliwia warstwy zawartość elementu podrzędnego, dzięki czemu więcej niż jeden element istnieje w jednym "komórki." <xref:System.Windows.Documents.Table> nie obsługuje tworzenie warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> można bezwzględnego względem obszaru ich granice "komórki". <xref:System.Windows.Documents.Table> nie obsługuje tej funkcji. Na koniec <xref:System.Windows.Controls.Grid> jest mniejsza waga niż <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Zachowanie ustalania rozmiaru kolumn i wierszy  
 Kolumn i wierszy zdefiniowany w ramach <xref:System.Windows.Controls.Grid> mogą wykorzystać <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru w celu dystrybucji proporcjonalnie pozostałe miejsce. Gdy <xref:System.Windows.GridUnitType.Star> został wybrany jako wysokość lub szerokość wiersz lub kolumnę, że kolumna lub wiersz otrzyma ważoną część pozostałego wolnego miejsca. Jest to contrast do <xref:System.Windows.GridUnitType.Auto>, która będzie dystrybuować miejsca równomiernie na podstawie rozmiaru zawartości w kolumny lub wiersza. Ta wartość jest wyrażona jako `*` lub `2*` przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. W pierwszym przypadku wiersz lub kolumnę, będzie odbierać razy jednego dostępnego miejsca, w drugim przypadku dwa razy i tak dalej. Łącząc proporcjonalnie dystrybucję miejsca z tej techniki <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartość `Stretch` jest możliwe do obszaru układu partycji według wartości procentowej miejsca na ekranie. <xref:System.Windows.Controls.Grid> jest panelu tylko układu, którą można dystrybuować miejsca w ten sposób.  
  
#### <a name="defining-and-using-a-grid"></a>Definiowanie i przy użyciu siatki  
 W poniższym przykładzie pokazano sposób tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doświadczyli na dostępne w oknie Uruchamianie [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Start menu.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Skompilowana aplikacja zwraca nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wygląda jak to.  
  
 ![Typowy Element siatki. ] (../../../../docs/framework/wpf/controls/media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umożliwia "stosu" elementów w kierunku przypisane. Domyślny kierunek stosu jest pionowy. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Właściwości może służyć do sterowania przepływem zawartości.  
  
#### <a name="stackpanel-vs-dockpanel"></a>Panel stosu vs. DockPanel  
 Mimo że <xref:System.Windows.Controls.DockPanel> można również "stosu" elementów podrzędnych <xref:System.Windows.Controls.DockPanel> i <xref:System.Windows.Controls.StackPanel> nie dostarczyło wyników analogiczne w niektórych przypadkach użycia. Na przykład kolejność elementów podrzędnych może mieć wpływ na ich rozmiar w <xref:System.Windows.Controls.DockPanel> , ale nie <xref:System.Windows.Controls.StackPanel>. Jest to spowodowane <xref:System.Windows.Controls.StackPanel> środki w kierunku układania w <xref:System.Double.PositiveInfinity>, podczas gdy <xref:System.Windows.Controls.DockPanel> mierzy tylko dostępny rozmiar.  
  
 W poniższym przykładzie pokazano różnicę klucza.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Różnica w sposób renderowania są widoczne w tym obrazie.  
  
 ![Zrzut ekranu: Vs Panel stosu. Zrzut ekranu DockPanel](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definiowanie i używanie Panel stosu  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.StackPanel> utworzyć zestaw przycisków znajduje się w pionie. Pozycjonowanie w poziomie, ustaw <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwości <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Skompilowana aplikacja zwraca nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wygląda jak to.  
  
 ![Typowy element Panel stosu. ] (../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostępne są także odmianą <xref:System.Windows.Controls.StackPanel> element, który automatycznie "Wirtualizuje" zawartość elementu podrzędnego powiązane z danymi. W tym kontekście wirtualizacji wyraz odwołuje się do technika, za pomocą którego podzbiór elementy zostaną wygenerowane na podstawie większą liczbę elementów danych oparte na elementy, które są widoczne na ekranie. Jest znacznym zarówno pod względem pamięci i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel> (za pośrednictwem funkcji udostępnianych przez usługę <xref:System.Windows.Controls.VirtualizingPanel>) oblicza widocznych elementów i współdziała z <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (takich jak <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ListView>) można tworzyć tylko elementy dla widocznych elementów.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Element zostanie automatycznie ustawione jako elementy hosta dla formantów, takich jak <xref:System.Windows.Controls.ListBox>. Gdy hosting danych powiązana kolekcji, zawartość automatycznie zostaje zwirtualizowany, tak długo, jak zawartość mieści się w granicach <xref:System.Windows.Controls.ScrollViewer>. To znacznie zwiększa wydajność, odnośnie do hostowania wielu elementów podrzędnych.  
  
 Następujący kod pokazuje sposób użycia <xref:System.Windows.Controls.VirtualizingStackPanel> jako hosta elementów. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> Dołączona właściwość musi mieć ustawioną `true` (domyślna) do wirtualizacji występuje.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> Służy do pozycjonować elementy podrzędne sekwencyjnie od lewej do prawej, łamiąc zawartość do następnego wiersza po osiągnięciu krawędzią kontenera nadrzędnego. Zawartość może być obiektowe poziomo czy pionowo. <xref:System.Windows.Controls.WrapPanel> jest przydatne w przypadku prostego przepływu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy. Można go również służyć do dotyczą wszystkich jego elementów podrzędnych uniform zmiany rozmiaru.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.WrapPanel> do wyświetlenia <xref:System.Windows.Controls.Button> formantów, które otaczają po upływie krawędź ich kontenera.  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Skompilowana aplikacja zwraca nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wygląda jak to.  
  
 ![Typowy WrapPanel Element. ] (../../../../docs/framework/wpf/controls/media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Elementy panelu zagnieżdżonych  
 <xref:System.Windows.Controls.Panel> elementy mogą być zagnieżdżane w sobie nawzajem w celu utworzenia złożonych układów. To może okazać się bardzo przydatne w sytuacjach, gdy jedna <xref:System.Windows.Controls.Panel> jest idealny dla części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale nie może zaspokoić potrzeby różnych części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Nie ma żadnego limitu praktyczne ilości zagnieżdżenia obsługujące aplikacji, jednak jest zazwyczaj najlepiej ograniczyć aplikacji do użycia tylko tych panele, które są rzeczywiście niezbędne dla żądanego układu. W wielu przypadkach <xref:System.Windows.Controls.Grid> element może być używany zamiast zagnieżdżonych panele z powodu jego elastyczność jako kontener układu. Umożliwia to zwiększenie wydajności aplikacji dzięki przechowywaniu niepotrzebnych elementów poza drzewa.  
  
 Poniższy przykład przedstawia sposób tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wykorzystuje zagnieżdżone <xref:System.Windows.Controls.Panel> elementów w celu uzyskania określonych układu. W tym przypadku <xref:System.Windows.Controls.DockPanel> element służy do zapewnienia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] struktury i zagnieżdżone <xref:System.Windows.Controls.StackPanel> elementów <xref:System.Windows.Controls.Grid>, a <xref:System.Windows.Controls.Canvas> służą do pozycjonować elementy podrzędne dokładnie w obrębie nadrzędnego <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Skompilowana aplikacja zwraca nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wygląda jak to.  
  
 ![Interfejs użytkownika, który korzysta z paneli zagnieżdżonych. ] (../../../../docs/framework/wpf/controls/media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Elementy panelu niestandardowych  
 Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera szereg kontroli elastyczny układ, niestandardowego układu zachowania robić również przez zastąpienie <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Niestandardowe zmiany rozmiaru i pozycjonowania można osiągnąć przez definiowanie nowych pozycjonowanie zachowania w ramach tych Przesłaniaj metody.  
  
 Podobnie, na podstawie zachowania niestandardowego układu klas pochodnych (takich jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.Grid>) może być zdefiniowany przez zastąpienie ich <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody.  
  
 Następujący kod przedstawia sposób tworzenia niestandardowego <xref:System.Windows.Controls.Panel> elementu. Nowy <xref:System.Windows.Controls.Panel>, zdefiniowanej jako `PlotPanel`, obsługuje rozmieszczania elementów podrzędnych za pomocą ustalony *x -* i *y -*współrzędnych. W tym przykładzie <xref:System.Windows.Shapes.Rectangle> elementu (tego nie pokazano) znajduje się w punkcie kreślenia 50 (*x*) do 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Aby wyświetlić bardziej złożone wdrożenia panelu niestandardowych, zobacz [Tworzenie niestandardowych zawartości zawijania przykładu panelu](http://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Obsługa lokalizacji/globalizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje wiele funkcji, które pomagają w przypadku tworzenia Lokalizowalny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Wszystkie elementy panelu natywnie obsługują <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość, która może służyć do dynamicznie ponownie przepływ zawartości na podstawie ustawień regionalnych lub języka użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A> Właściwość zapewnia mechanizm, który umożliwia deweloperom aplikacji do przewidywania potrzeb zlokalizowane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Przy użyciu <xref:System.Windows.SizeToContent.WidthAndHeight> wartość tej właściwości elementu nadrzędnego <xref:System.Windows.Window> zawsze rozmiary dynamicznie w celu dopasowania do zawartości i nie jest ograniczane przez sztuczne ograniczenia szerokość lub wysokość.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, i <xref:System.Windows.Controls.StackPanel> powinno się wszystkie do zlokalizowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas> jest dobrym rozwiązaniem, jednak, ponieważ jego umieszcza zawartości absolutnie, dzięki czemu trudne do zlokalizowania.  
  
 Aby uzyskać dodatkowe informacje na temat tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji za pomocą Lokalizowalny [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s, zobacz [użycie automatycznego układu omówienie](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Przykładu z galerii układu WPF](http://go.microsoft.com/fwlink/?LinkID=160054)  
 [Układ](../../../../docs/framework/wpf/advanced/layout.md)  
 [Przykładu z galerii formantów WPF](http://go.microsoft.com/fwlink/?LinkID=160053)  
 [Przegląd wyrównania, marginesów i wypełnień](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Tworzenie niestandardowych przykładu panelu zawijania zawartości](http://go.microsoft.com/fwlink/?LinkID=159979)  
 [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Przegląd używania automatycznego układu](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
