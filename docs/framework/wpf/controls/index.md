---
title: Formanty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 42596c8adf1b8b27f250fa7a3cf6cc173a63e2eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459447"
---
# <a name="controls"></a>Formanty
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dostarcza wielu wspólnych składników interfejsu użytkownika, które są używane w prawie każdej aplikacji systemu Windows, takiej jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>i <xref:System.Windows.Controls.ListBox>. Historycznie te obiekty zostały określone jako kontrolki. Mimo że zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK nadal używa terminu "Control" do swobodnego oznaczania każdej klasy, która reprezentuje widoczny obiekt w aplikacji, należy zauważyć, że Klasa nie musi dziedziczyć z klasy <xref:System.Windows.Controls.Control>, aby mieć widoczną obecność. Klasy dziedziczące z klasy <xref:System.Windows.Controls.Control> zawierają <xref:System.Windows.Controls.ControlTemplate>, co umożliwia konsumentowi kontrolce radykalne Zmienianie wyglądu kontrolki bez konieczności tworzenia nowej podklasy.  W tym temacie omówiono sposób, w jaki formanty (które dziedziczą z klasy <xref:System.Windows.Controls.Control> i te, które nie są) są często używane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Tworzenie wystąpienia kontrolki  
 Można dodać kontrolkę do aplikacji przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu.  Poniższy przykład pokazuje, jak utworzyć prostą aplikację, która monituje użytkownika o podanie ich imienia i nazwiska.  Ten przykład tworzy sześć kontrolek: dwie etykiety, dwa pola tekstowe i dwa przyciski w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Wszystkie kontrolki można tworzyć podobnie.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 W poniższym przykładzie jest tworzona ta sama aplikacja w kodzie. W przypadku zwięzłości tworzenie <xref:System.Windows.Controls.Grid>, `grid1`, zostało wyłączone z przykładu. `grid1` ma te same definicje kolumn i wierszy, jak pokazano w powyższym przykładzie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Zmiana wyglądu kontrolki  
 Typowym sposobem zmiany wyglądu kontrolki jest dopasowanie wyglądu i sposobu działania aplikacji. Wygląd formantu można zmienić, wykonując jedną z następujących czynności, w zależności od tego, co chcesz osiągnąć:  
  
- Zmień wartość właściwości formantu.  
  
- Utwórz <xref:System.Windows.Style> dla kontrolki.  
  
- Utwórz nowy <xref:System.Windows.Controls.ControlTemplate> dla kontrolki.  
  
### <a name="changing-a-controls-property-value"></a>Zmiana wartości właściwości kontrolki  
 Wiele kontrolek ma właściwości, które umożliwiają zmianę sposobu wyświetlania kontrolki, takiej jak <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>. Właściwości wartości można ustawić zarówno w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak i w kodzie. Poniższy przykład ustawia właściwości <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>i <xref:System.Windows.Controls.Control.FontWeight%2A> na <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Poniższy przykład ustawia te same właściwości w kodzie.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Tworzenie stylu kontrolki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daje możliwość określenia wyglądu hurtowników, zamiast ustawiania właściwości dla każdego wystąpienia w aplikacji, tworząc <xref:System.Windows.Style>. Poniższy przykład tworzy <xref:System.Windows.Style>, który jest stosowany do poszczególnych <xref:System.Windows.Controls.Button> w aplikacji. definicje <xref:System.Windows.Style> są zwykle zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w <xref:System.Windows.ResourceDictionary>, takie jak Właściwość <xref:System.Windows.FrameworkElement.Resources%2A> <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Można również zastosować styl tylko do niektórych formantów określonego typu przez przypisanie klucza do stylu i określenie tego klucza we właściwości `Style` formantu.  Aby uzyskać więcej informacji na temat stylów, zobacz [Style i tworzenia szablonów](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Tworzenie ControlTemplate  
 <xref:System.Windows.Style> umożliwia ustawianie właściwości w wielu kontrolkach w danym momencie, ale czasami warto dostosować wygląd <xref:System.Windows.Controls.Control> poza tym, co można zrobić, tworząc <xref:System.Windows.Style>. Klasy dziedziczące z klasy <xref:System.Windows.Controls.Control> mają <xref:System.Windows.Controls.ControlTemplate>, które definiują strukturę i wygląd <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Właściwość <xref:System.Windows.Controls.Control> jest publiczna, więc można <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate>, która jest inna niż domyślna. Można często określić nowe <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Control> zamiast dziedziczyć z kontrolki, aby dostosować wygląd <xref:System.Windows.Controls.Control>.  
  
 Rozważmy bardzo powszechną kontrolę, <xref:System.Windows.Controls.Button>.  Podstawowym zachowaniem <xref:System.Windows.Controls.Button> jest umożliwienie aplikacji podjęcia pewnej akcji po jej kliknięciu przez użytkownika.  Domyślnie <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pojawia się jako podniesiony prostokąt.  Podczas tworzenia aplikacji możesz chcieć wykorzystać zachowanie <xref:System.Windows.Controls.Button>— to jest, poprzez obsłużenie zdarzenia kliknięcia przycisku — ale można zmienić wygląd przycisku poza tym, co można zrobić, zmieniając właściwości przycisku.  W takim przypadku można utworzyć nowe <xref:System.Windows.Controls.ControlTemplate>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> tworzy <xref:System.Windows.Controls.Button> z zaokrąglonymi rogami i tłem gradientowym.  <xref:System.Windows.Controls.ControlTemplate> zawiera <xref:System.Windows.Controls.Border>, których <xref:System.Windows.Controls.Border.Background%2A> jest <xref:System.Windows.Media.LinearGradientBrush> z dwoma obiektami <xref:System.Windows.Media.GradientStop>.  Pierwszy <xref:System.Windows.Media.GradientStop> używa powiązania danych, aby powiązać Właściwość <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.GradientStop> z kolorem tła przycisku.  Po ustawieniu właściwości <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>, kolor tej wartości będzie używany jako pierwszy <xref:System.Windows.Media.GradientStop>. Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md). W przykładzie tworzony jest również <xref:System.Windows.Trigger>, która zmienia wygląd <xref:System.Windows.Controls.Button>, gdy <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Aby przykład działał prawidłowo, właściwość <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> musi być ustawiona na <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Możesz subskrybować zdarzenie kontrolki za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu, ale można obsłużyć tylko zdarzenie w kodzie.  Poniższy przykład pokazuje, jak subskrybować zdarzenie `Click` <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Poniższy przykład obsługuje zdarzenie `Click` <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Zawartość rozbudowana w kontrolkach  
 Większość klas, które dziedziczą z klasy <xref:System.Windows.Controls.Control>, ma pojemność do przechowywania zawartości bogatej. Na przykład <xref:System.Windows.Controls.Label> może zawierać dowolny obiekt, taki jak ciąg, <xref:System.Windows.Controls.Image>lub <xref:System.Windows.Controls.Panel>.  Poniższe klasy zapewniają obsługę bogatej zawartości i działają jako klasy bazowe dla większości formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Controls.ContentControl>— przykłady klas, które dziedziczą z tej klasy, to <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>i <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>— przykłady klas, które dziedziczą z tej klasy, to <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>i <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>— przykłady klas, które dziedziczą z tej klasy, to <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>i <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>— przykłady klas, które dziedziczą z tej klasy, to <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>i <xref:System.Windows.Controls.ToolBar>.  

 Aby uzyskać więcej informacji na temat tych klas bazowych, zobacz [WPF content model](wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Kontrolki według kategorii](controls-by-category.md)
- [Biblioteka kontrolek](control-library.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Dane wejściowe](../advanced/input-wpf.md)
- [Włączanie polecenia](../advanced/how-to-enable-a-command.md)
- [Przewodnik: tworzenie niestandardowego przycisku animowanego](walkthroughs-create-a-custom-animated-button.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
