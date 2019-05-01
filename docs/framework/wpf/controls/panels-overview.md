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
ms.openlocfilehash: 946e0f5ee90235498b8089732ae526ab6f35665c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051029"
---
# <a name="panels-overview"></a>Przegląd Panele
<xref:System.Windows.Controls.Panel> elementy są składniki, które kontrolują renderowanie elementów — ich rozmiar i wymiarów, ich pozycji i rozmieszczenie ich zawartość elementu podrzędnego. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Zawiera szereg wstępnie zdefiniowanych <xref:System.Windows.Controls.Panel> elementów, a także możliwość utworzenia niestandardowych <xref:System.Windows.Controls.Panel> elementów.  
  
 Ten temat zawiera następujące sekcje.  
  
- [Klasa panelu](#Panels_view_from_10000_feet)  
  
- [Panel elementu wspólnych elementów członkowskich](#Panels_declared_members)  
  
- [Elementy panelu pochodne](#Panels_derived_elements)  
  
- [Panele interfejsu użytkownika](#Panels_main_UI_elements)  
  
- [Panel zagnieżdżonych elementów](#Panels_nested_panel_elements)  
  
- [Elementy niestandardowe panelu](#Panels_custom_panel_elements)  
  
- [Obsługa lokalizacji/globalizacji](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Klasa panelu  
 <xref:System.Windows.Controls.Panel> jest klasą bazową dla wszystkich elementów, które zapewniają układu obsługi w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Pochodne <xref:System.Windows.Controls.Panel> służą elementów to pozycjonowania i rozmieszczania elementów w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obejmuje kompleksowym pakietem implementacje pochodnej panelu, umożliwiające wiele złożonych układów. Te klasy pochodne ujawnić właściwości i metod, które umożliwiają większość standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy. Deweloperzy, którzy nie mogą odnaleźć zachowanie rozmieszczenie podrzędne, które odpowiadają ich potrzebom można tworzyć nowe układy przez zastąpienie <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Aby uzyskać więcej informacji na temat zachowania układu niestandardowego, zobacz [niestandardowe elementy panelu](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Panel wspólnych elementów członkowskich  
 Wszystkie <xref:System.Windows.Controls.Panel> elementów pomocy technicznej podstawowy, rozmiar i położenie właściwości zdefiniowane przez <xref:System.Windows.FrameworkElement>, w tym <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, i <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Aby uzyskać dodatkowe informacje na temat właściwości zdefiniowane przez ustawienia <xref:System.Windows.FrameworkElement>, zobacz [wyrównanie, marginesy i dopełnienie Przegląd](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> udostępnia dodatkowe właściwości, które mają krytyczne znaczenie w znajomość i wykorzystanie układu. <xref:System.Windows.Controls.Panel.Background%2A> Właściwość jest używana, aby wypełnił obszar między granicami elementu panelu pochodne z <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A> reprezentuje kolekcję elementów podrzędnych, <xref:System.Windows.Controls.Panel> składa się z. <xref:System.Windows.Controls.Panel.InternalChildren%2A> reprezentuje zawartość <xref:System.Windows.Controls.Panel.Children%2A> kolekcji, a także tych członków, generowane przez powiązanie danych. Oba składają się z <xref:System.Windows.Controls.UIElementCollection> elementów podrzędnych, obsługiwany przez nadrzędne <xref:System.Windows.Controls.Panel>.  
  
 Również panelu ujawnia <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> dołączona właściwość, który może służyć do osiągnięcia warstwowej kolejność pochodnej <xref:System.Windows.Controls.Panel>. Członkowie zespołu <xref:System.Windows.Controls.Panel.Children%2A> kolekcji z większym <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartości są wyświetlane przed o niższych <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> wartość. Jest to szczególnie przydatne dla paneli takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.Grid> umożliwiające elementów podrzędnych na udostępnianie tej samej przestrzeni współrzędnych.  
  
 <xref:System.Windows.Controls.Panel> definiuje również <xref:System.Windows.Controls.Panel.OnRender%2A> metody, która może służyć do zastępowania domyślnego zachowania prezentacji <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Elementy panelu pochodnej Wykorzystaj rozbudowane dołączone właściwości. Dołączona właściwość jest formą specjalistyczne właściwości zależności, która nie ma konwencjonalne [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwość "otoki". Dołączone właściwości mają specjalne składni w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], które są widoczne w kilka przykładów, które należy wykonać.  
  
 Jeden cel dołączoną właściwość jest umożliwienie podrzędnych elementów do przechowywania unikatowych wartości właściwości, który faktycznie jest zdefiniowany przez element nadrzędny. Aplikacja ta funkcja ma elementy podrzędne, które powiadamia element nadrzędny, jak mają być przedstawiane w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], który jest bardzo przydatne w przypadku układu aplikacji. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Elementy panelu pochodne  
 Wiele obiektów pochodzić od <xref:System.Windows.Controls.Panel>, ale nie wszystkie z nich są przeznaczone do użytku jako głównego układu dostawców. Istnieją sześciu klas zdefiniowanych panelu (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, i <xref:System.Windows.Controls.WrapPanel>) te zostały zaprojektowane specjalnie do tworzenia aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Każdy element Panelu hermetyzuje swój własny specjalne funkcje, jak pokazano w poniższej tabeli.  
  
|Nazwa elementu|Panel interfejsu użytkownika?|Opis|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Tak|Definiuje obszar, w którym możesz jawnie pozycjonować elementy podrzędne współrzędnymi względem <xref:System.Windows.Controls.Canvas> obszaru.|  
|<xref:System.Windows.Controls.DockPanel>|Tak|Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub pionie, względem siebie.|  
|<xref:System.Windows.Controls.Grid>|Tak|Definiuje elastyczny obszar siatki składający się z kolumnami i wierszami. Elementy podrzędne <xref:System.Windows.Controls.Grid> umieszczony dokładnie przy użyciu <xref:System.Windows.FrameworkElement.Margin%2A> właściwości.|  
|<xref:System.Windows.Controls.StackPanel>|Yes|Rozmieszcza elementy podrzędne w jednej linii, która może być zorientowana poziomo czy pionowo.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Nie|Obsługuje układ przycisków karty w <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nie|Organizuje zawartości w ramach <xref:System.Windows.Controls.ToolBar> kontroli.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Nie|<xref:System.Windows.Controls.Primitives.UniformGrid> Służy do Rozmieść elementy podrzędne w siatce, ze wszystkimi rozmiarami równy komórki.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Nie|Udostępnia klasę bazową dla paneli, które mogą "Wirtualizacja" ich elementy podrzędne kolekcji.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Tak|Rozmieszcza i Wirtualizuje zawartość w jednym wierszu zorientowanej na poziomo czy pionowo.|  
|<xref:System.Windows.Controls.WrapPanel>|Tak|<xref:System.Windows.Controls.WrapPanel> Ustawia elementy podrzędne na kolejnych pozycjach od od lewej do prawej, istotne zawartości do następnego wiersza na krawędzi zawierającego pole. Kolejne porządkowanie się dzieje sekwencyjnie od góry do dołu lub od prawej do lewej w zależności od wartości <xref:System.Windows.Controls.WrapPanel.Orientation%2A> właściwości.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Panele interfejsu użytkownika  
 Są dostępne w sześciu klas panelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , są zoptymalizowane pod kątem obsługi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, i <xref:System.Windows.Controls.WrapPanel>. Te elementy panelu są łatwe w użyciu, wszechstronne i rozszerzalny, w przypadku większości aplikacji.  
  
 Każdy pochodne <xref:System.Windows.Controls.Panel> element traktuje ograniczenia rozmiaru inaczej. Opis sposobu <xref:System.Windows.Controls.Panel> obsługuje ograniczenia w poziomie lub pionie kierunku mogą w praktyce uniemożliwić układ bardziej przewidywalne.  
  
|**Panel nazwa**|**x-Dimension**|**Wymiar y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Ograniczone do zawartości|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.DockPanel>|Ograniczone|Ograniczone|  
|<xref:System.Windows.Controls.StackPanel> (Orientacji pionowej)|Ograniczone|Ograniczone do zawartości|  
|<xref:System.Windows.Controls.StackPanel> (Orientacji poziomej)|Ograniczone do zawartości|Ograniczone|  
|<xref:System.Windows.Controls.Grid>|Ograniczone|Ograniczone, z wyjątkiem przypadków, gdy <xref:System.Windows.GridUnitType.Auto> dotyczą wierszy i kolumn|  
|<xref:System.Windows.Controls.WrapPanel>|Ograniczone do zawartości|Ograniczone do zawartości|  
  
 Bardziej szczegółowe opisy i przykłady użycia każdego z tych elementów można znaleźć poniżej.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Kanwa  
 <xref:System.Windows.Controls.Canvas> Element włącza rozmieszczenia zawartości zgodnie z bezwzględną *x -* i *y -* współrzędnych. Elementy mogą znajdować się na środku odrębnej lokalizacji; lub, jeśli elementy zajmować takich samych współrzędnych, kolejność, w jakiej występują w znacznikach określa kolejność, w której elementy są wyświetlane.  
  
 <xref:System.Windows.Controls.Canvas> udostępnia najbardziej elastyczna obsługa układów dla dowolnego <xref:System.Windows.Controls.Panel>. Właściwości Height i Width są używane do definiowania obszar na kanwie, a elementy wewnątrz przypisanych współrzędne bezwzględne względem pola elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Cztery dołączone właściwości, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, Zezwalaj na dokładnej kontroli położenie obiektu <xref:System.Windows.Controls.Canvas>, umożliwiając deweloperom pozycjonowania i rozmieszczania elementów dokładnie na ekranie.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds w obrębie obszaru roboczego  
 <xref:System.Windows.Controls.Canvas> można pozycjonować elementy podrzędne w dowolnym miejscu na ekranie, nawet na współrzędne, które znajdują się poza własne zdefiniowane <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A>. Ponadto <xref:System.Windows.Controls.Canvas> nie dotyczy rozmiar jego elementów podrzędnych. W rezultacie, istnieje możliwość, że element podrzędny do innych elementów poza prostokąt otaczający element nadrzędny overdraw <xref:System.Windows.Controls.Canvas>. Domyślne zachowanie <xref:System.Windows.Controls.Canvas> jest umożliwienie elementów podrzędnych do narysowania poza granice elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Jeśli to zachowanie jest niepożądany, <xref:System.Windows.UIElement.ClipToBounds%2A> właściwość może być ustawiona na `true`. Powoduje to, że <xref:System.Windows.Controls.Canvas> do klipu swój własny rozmiar. <xref:System.Windows.Controls.Canvas> jest elementem tylko układ, który zezwala na elementy podrzędne do narysowania poza jej granicami.  
  
 To zachowanie jest graficznie zilustrowane w [przykład porównania właściwości szerokości](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definiowanie i korzystanie z obszaru roboczego  
 A <xref:System.Windows.Controls.Canvas> mogą być utworzone przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu. Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Controls.Canvas> absolutnie położenie zawartości. Ten kod tworzy trzy pola 100 pikseli. Pierwszy prostokąt jest czerwony, a jego lewym górnym rogu (*x, y*) pozycja jest określony jako (0, 0). Drugi kwadrat jest zielony, a jego pozycja w lewym górnym rogu (100, 100), tuż poniżej, a po prawej stronie części pierwszego prostokąta. Trzeci kwadrat jest niebieski, a jego pozycja w lewym górnym rogu (50, 50), dlatego obejmujący quadrant prawej dolnej części pierwszego prostokąta i quadrant lewego górnego drugiego. Ponieważ trzeci kwadrat jest poukładany ostatniego, prawdopodobnie na podstawie dwa pola — oznacza to, nakładających się części założono kolor trzecim polu.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Skompilowaną aplikację daje nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do następującego.  
  
 ![Typowy Element roboczy. ](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Element używa <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> dołączonych właściwości ustawione w zawartości elementów podrzędnych, aby umieścić zawartość wzdłuż krawędzi kontenera. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ustawiono <xref:System.Windows.Controls.Dock.Top> lub <xref:System.Windows.Controls.Dock.Bottom>, umieszcza jego elementów podrzędnych, powyżej lub poniżej siebie nawzajem. Gdy <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ustawiono <xref:System.Windows.Controls.Dock.Left> lub <xref:System.Windows.Controls.Dock.Right>, umieszcza jego elementy podrzędne w lewo lub prawo do siebie nawzajem. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> Właściwość określa położenie elementu końcowego dodany jako element podrzędny elementu <xref:System.Windows.Controls.DockPanel>.  
  
 Możesz użyć <xref:System.Windows.Controls.DockPanel> do pozycji grupy pokrewnych formantów, takich jak zestaw przycisków. Alternatywnie służy do tworzenia w "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], podobnie jak w [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>Ustalanie rozmiaru zawartości  
 Jeśli jej <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości nie są określone, <xref:System.Windows.Controls.DockPanel> rozmiarów do jego zawartości. Rozmiar można zwiększyć lub zmniejszyć aby pomieścić rozmiar jego elementy podrzędne. Jednakże, gdy te właściwości są określone i nie ma już miejsca dla następnego elementu określony podrzędny <xref:System.Windows.Controls.DockPanel> nie wyświetla tego elementu podrzędnego lub elementy podrzędne na kolejnych i nie można mierzyć elementy podrzędne kolejne.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> elementu "wypełni" pozostało, nieprzydzielone miejsce. Jeśli to zachowanie jest niepożądany, należy ustawić <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> właściwość `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definiowanie i korzystanie z DockPanel  
 Poniższy przykład pokazuje, jak partycji przy użyciu miejsca <xref:System.Windows.Controls.DockPanel>. Pięć <xref:System.Windows.Controls.Border> elementy są dodawane jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>. Każda używa różnych właściwości pozycjonowania <xref:System.Windows.Controls.DockPanel> do miejsca na partycji. Ostatnim elementem "wypełnia" pozostała, nieprzydzielone miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Skompilowaną aplikację daje nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do następującego.  
  
 ![Typowy scenariusz DockPanel. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Siatka  
 <xref:System.Windows.Controls.Grid> Element scala funkcje pozycjonowanie absolutne i kontroli danych tabelarycznych. A <xref:System.Windows.Controls.Grid> pozwala na łatwe pozycji i elementy stylu. <xref:System.Windows.Controls.Grid> można zdefiniować elastyczne wierszy i kolumn grupowania, a nawet udostępnia mechanizm do udostępnienia informacji ustalania rozmiaru między wieloma <xref:System.Windows.Controls.Grid> elementów.  
  
#### <a name="how-is-grid-different-from-table"></a>Czym różni się siatki z tabeli?  
 <xref:System.Windows.Documents.Table> i <xref:System.Windows.Controls.Grid> udostępnianie niektóre typowe funkcje, ale każdy jest najbardziej odpowiednie dla różnych scenariuszy. A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w ramach dowolnej zawartości (zobacz [Przegląd dokumentu przepływu](../advanced/flow-document-overview.md) więcej informacji na temat zawartości przepływu). Siatki najlepiej sprawdzają się wewnątrz formularzy (zasadniczo dowolne miejsce poza przepływ zawartości). W ramach <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> obsługuje przepływ zawartości zachowań, takich jak podział na strony, ze zmianą ułożenia kolumny i zawartości zaznaczenia podczas <xref:System.Windows.Controls.Grid> nie. A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej nadaje się poza <xref:System.Windows.Documents.FlowDocument> wiele powodów, takich jak <xref:System.Windows.Controls.Grid> dodaje elementy w oparciu o indeks wierszy i kolumn <xref:System.Windows.Documents.Table> nie. <xref:System.Windows.Controls.Grid> Elementu umożliwia warstwowe zawartość elementu podrzędnego, dzięki czemu więcej niż jeden element istnieje w jednej "komórki." <xref:System.Windows.Documents.Table> nie obsługują warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> można pozycjonowane absolutnie względem pola ich granice "komórki". <xref:System.Windows.Documents.Table> nie obsługuje tej funkcji. Na koniec <xref:System.Windows.Controls.Grid> jest mniejsza waga niż <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Zachowanie zmiany rozmiaru kolumn i wierszy  
 Kolumn i wierszy zdefiniowany w ramach <xref:System.Windows.Controls.Grid> korzystać z zalet <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru w celu dystrybucji proporcjonalną ilość wolnego miejsca. Gdy <xref:System.Windows.GridUnitType.Star> jest wybrany jako wysokości lub szerokości wiersza lub kolumny, że kolumny lub wiersza otrzyma ważona część pozostałego dostępnego miejsca. Jest to w przeciwieństwie do <xref:System.Windows.GridUnitType.Auto>, która będzie dystrybuować równomiernie na podstawie rozmiaru zawartości w kolumnie lub wierszu miejsca. Ta wartość jest wyrażona jako `*` lub `2*` przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. W pierwszym przypadku wiersza lub kolumny będą otrzymywać razy jednego dostępnego miejsca, w drugim przypadku dwa razy i tak dalej. Łącząc proporcjonalnie dystrybucję miejsca z tej techniki <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartość `Stretch` jest możliwe do obszaru układu partycji według wartości procentowej miejsca na ekranie. <xref:System.Windows.Controls.Grid> jest panel tylko układ, który można dystrybuować miejsca w ten sposób.  
  
#### <a name="defining-and-using-a-grid"></a>Definiowanie i korzystanie z siatki  
 Poniższy przykład pokazuje, jak tworzyć [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doświadczyli na dostępne w oknie Uruchamianie [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Start menu.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Skompilowaną aplikację daje nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do następującego.  
  
 ![Typowy Element siatki. ](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> umożliwia "stos" elementy w kierunku przypisane. Domyślny kierunek stosu jest pionowy. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Właściwość może służyć do sterowania przepływem zawartości.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel programu vs. DockPanel  
 Mimo że <xref:System.Windows.Controls.DockPanel> można również "stos" elementy podrzędne <xref:System.Windows.Controls.DockPanel> i <xref:System.Windows.Controls.StackPanel> nie dawać analogiczne wyników w niektórych scenariuszach użycia. Na przykład kolejność elementów podrzędnych może mieć wpływ na ich rozmiar w <xref:System.Windows.Controls.DockPanel> , ale nie <xref:System.Windows.Controls.StackPanel>. Jest to spowodowane <xref:System.Windows.Controls.StackPanel> miary w kierunku układania na <xref:System.Double.PositiveInfinity>, podczas gdy <xref:System.Windows.Controls.DockPanel> mierzy tylko dostępny rozmiar.  
  
 W poniższym przykładzie pokazano to główną różnicą.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Różnica w zachowaniu renderowania są widoczne na tej ilustracji.  
  
 ![Zrzut ekranu: StackPanel programu vs. Zrzut ekranu DockPanel](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definiowanie i korzystanie z StackPanel  
 Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Controls.StackPanel> utworzyć zestaw przycisków umieszczony w pionie. Poziome położenie, ustaw <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwość <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Skompilowaną aplikację daje nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do następującego.  
  
 ![Typowy element StackPanel. ](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również odmianą <xref:System.Windows.Controls.StackPanel> element, który automatycznie "Wirtualizuje" zawartość elementu podrzędnego powiązanych z danymi. W tym kontekście słowo wirtualizacji dotyczy to technika, za pomocą której podzbiór elementów są generowane na podstawie większej liczby elementów danych na podstawie elementy, które są widoczne na ekranie. Jest intensywna, zarówno pod względem pamięci i procesora, aby generować dużą liczbę elementów interfejsu użytkownika, gdy tylko kilka może znajdować się na ekranie w danym momencie. <xref:System.Windows.Controls.VirtualizingStackPanel> (za pośrednictwem funkcje udostępniane przez <xref:System.Windows.Controls.VirtualizingPanel>) oblicza widocznych elementów i projektów w programach <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (takie jak <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ListView>) można tworzyć tylko elementy widoczne elementy.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Element zostanie automatycznie ustawione jako elementów hosta dla formantów, takich jak <xref:System.Windows.Controls.ListBox>. Gdy hosting danych powiązana kolekcji, zawartość automatycznie jest Zwirtualizowana, tak długo, jak zawartości znajduje się w granicach <xref:System.Windows.Controls.ScrollViewer>. Znacznie poprawia to wydajność w przypadku hostowania wielu elementów podrzędnych.  
  
 Następujący kod pokazuje sposób użycia <xref:System.Windows.Controls.VirtualizingStackPanel> jako hosta elementów. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> Dołączonej właściwości musi być równa `true` (domyślna) do wirtualizacji wystąpienia.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> Służy do pozycjonować elementy podrzędne na kolejnych pozycjach od lewej do prawej, istotnej zawartości do następnego wiersza po osiągnięciu krawędzią jej kontenera nadrzędnego. Zawartości są rozmieszczane w poziomie lub pionie. <xref:System.Windows.Controls.WrapPanel> jest przydatne w przypadku prostego przepływu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenariuszy. Może również służyć dotyczą rozmiarów jednolitego wszystkie jego elementy podrzędne.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.WrapPanel> do wyświetlenia <xref:System.Windows.Controls.Button> formantów, które umieszczają w otoce po osiągnięciu krawędź ich kontenera.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Skompilowaną aplikację daje nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do następującego.  
  
 ![Typowy WrapPanel Element. ](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Panel zagnieżdżonych elementów  
 <xref:System.Windows.Controls.Panel> elementy mogą być zagnieżdżone wewnątrz innych w celu tworzenia złożonych układów. Można to potwierdzić bardzo przydatne w sytuacjach, gdy jedna <xref:System.Windows.Controls.Panel> jest idealny dla części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ale może nie spełniać wymagań różnych części [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Nie ma żadnych praktyczne limitu liczby zagnieżdżeń, który może obsługiwać aplikację, jednak jest zazwyczaj najlepiej ograniczyć aplikację do użycia tylko tych zespołów, które są rzeczywiście konieczne, aby uzyskać żądany układ. W wielu przypadkach <xref:System.Windows.Controls.Grid> element może być używany zamiast paneli zagnieżdżonych ze względu na jego elastyczność jako kontener układu. Umożliwia to zwiększenie wydajności w aplikacji poprzez zapewnienie zbędnych elementów poza drzewa.  
  
 Poniższy przykład przedstawia sposób tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wykorzystuje zagnieżdżone <xref:System.Windows.Controls.Panel> elementy w celu uzyskania określonego układu. W tym konkretnym przypadku <xref:System.Windows.Controls.DockPanel> element służy do zapewnienia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] struktury i zagnieżdżone <xref:System.Windows.Controls.StackPanel> elementów, <xref:System.Windows.Controls.Grid>, a <xref:System.Windows.Controls.Canvas> służą do pozycjonować elementy podrzędne dokładnie nadrzędnym <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Skompilowaną aplikację daje nową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do następującego.  
  
 ![Interfejs użytkownika, który korzysta z zalet paneli zagnieżdżonych. ](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Elementy niestandardowe panelu  
 Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje szereg elastycznym układzie formanty, układ niestandardowy zachowania również można osiągnąć przez zastąpienie <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody. Niestandardowe, rozmiar i położenie można osiągnąć przez definiowanie nowego położenia zachowań w ramach tych Przesłaniaj metody.  
  
 Podobnie, zachowania układu niestandardowego na podstawie klas pochodnych (takich jak <xref:System.Windows.Controls.Canvas> lub <xref:System.Windows.Controls.Grid>) można zdefiniować przez zastąpienie ich <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> i <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody.  
  
 Następujący kod pokazuje, jak utworzyć niestandardową <xref:System.Windows.Controls.Panel> elementu. Ta nowa <xref:System.Windows.Controls.Panel>, jest definiowany jako `PlotPanel`, obsługuje pozycjonowanie elementów podrzędnych za pomocą zakodowanych *x -* i *y -* współrzędnych. W tym przykładzie <xref:System.Windows.Shapes.Rectangle> element (niewyświetlany) jest pozycjonowany w momencie wykres 50 (*x*) do 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Aby wyświetlić bardziej złożonych implementacji niestandardowy panel, zobacz [tworzenie przykładowej panelu niestandardowej zawartości zawijania](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Obsługa lokalizacji/globalizacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje wiele funkcji, które pomagają w tworzeniu Lokalizowalny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Wszystkie elementy panelu w sposób natywny obsługują <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość, która może służyć do dynamicznie ponownie przepływ zawartości na podstawie ustawień regionalnych lub języka użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A> Właściwość udostępnia mechanizm, który umożliwia programistom przewidywać potrzeby zlokalizowane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Za pomocą <xref:System.Windows.SizeToContent.WidthAndHeight> wartość tej właściwości elementu nadrzędnego <xref:System.Windows.Window> zawsze rozmiarach dynamicznie w celu dopasowania do zawartości i nie jest ograniczony przez sztuczne ograniczenia szerokość lub wysokość.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, i <xref:System.Windows.Controls.StackPanel> powinno się wszystkie do zlokalizowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas> jest dobrym rozwiązaniem, jednak, ponieważ jego umieszcza zawartości oczywiście, dzięki czemu trudne do zlokalizowania.  
  
 Aby uzyskać dodatkowe informacje na temat tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji przy użyciu możliwych do zlokalizowania [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s, zobacz [— Przegląd Użyj automatycznego układu](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Przykład WPF układu galerii](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Układ](../advanced/layout.md)
- [Przykładu z galerii kontrolki WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Przegląd wyrównania, marginesów i wypełnień](../advanced/alignment-margins-and-padding-overview.md)
- [Tworzenie niestandardowych przykładowej panelu zawijania zawartości](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md)
- [Przegląd używania automatycznego układu](../advanced/use-automatic-layout-overview.md)
- [Układ i projekt](../advanced/optimizing-performance-layout-and-design.md)
