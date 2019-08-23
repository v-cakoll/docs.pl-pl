---
title: Formanty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: faa1fbad85acf5788c10de7750c6a7c32b535bf5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957038"
---
# <a name="controls"></a>Formanty
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]dostarcza wiele typowych składników interfejsu użytkownika, które są używane w prawie każdej aplikacji systemu Windows, takiej jak <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Menu>,, i <xref:System.Windows.Controls.ListBox>. Historycznie te obiekty zostały określone jako kontrolki. Mimo że <xref:System.Windows.Controls.Control> zestaw SDK kontynuuje używanie terminu "kontrola" do swobodnego oznaczania każdej klasy, która reprezentuje widoczny obiekt w aplikacji, należy zauważyć, że Klasa nie musi dziedziczyć z klasy, aby mieć widoczną obecność. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Klasy dziedziczące z <xref:System.Windows.Controls.Control> klasy zawierają element <xref:System.Windows.Controls.ControlTemplate>, który umożliwia konsumentowi kontrolce radykalnie Zmienianie wyglądu kontrolki bez konieczności tworzenia nowej podklasy.  W tym temacie omówiono sposób, w jaki formanty (zarówno te, <xref:System.Windows.Controls.Control> które dziedziczą z klasy, jak i te, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nie są) są często używane w programie.  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Tworzenie wystąpienia kontrolki  
 Możesz dodać formant do aplikacji przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] albo kodu.  Poniższy przykład pokazuje, jak utworzyć prostą aplikację, która monituje użytkownika o podanie ich imienia i nazwiska.  Ten przykład tworzy sześć kontrolek: dwie etykiety, dwa pola tekstowe i dwa przyciski w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Wszystkie kontrolki można tworzyć podobnie.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 W poniższym przykładzie jest tworzona ta sama aplikacja w kodzie. W przypadku zwięzłości Tworzenie elementu <xref:System.Windows.Controls.Grid>, `grid1`zostało wyłączone z przykładu. `grid1`zawiera te same definicje kolumn i wierszy, jak pokazano w powyższym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykładzie.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Zmiana wyglądu kontrolki  
 Typowym sposobem zmiany wyglądu kontrolki jest dopasowanie wyglądu i sposobu działania aplikacji. Wygląd formantu można zmienić, wykonując jedną z następujących czynności, w zależności od tego, co chcesz osiągnąć:  
  
- Zmień wartość właściwości formantu.  
  
- <xref:System.Windows.Style> Utwórz dla kontrolki.  
  
- Utwórz nową <xref:System.Windows.Controls.ControlTemplate> kontrolkę.  
  
### <a name="changing-a-controls-property-value"></a>Zmiana wartości właściwości kontrolki  
 Wiele kontrolek ma właściwości, które umożliwiają zmianę sposobu wyświetlania kontrolki, <xref:System.Windows.Controls.Control.Background%2A> na przykład a. <xref:System.Windows.Controls.Button> Można ustawić właściwości wartości w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kodzie. Poniższy przykład <xref:System.Windows.Controls.Control.Background%2A>ustawia właściwości, <xref:System.Windows.Controls.Control.FontWeight%2A> <xref:System.Windows.Controls.Control.FontSize%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], i w w. <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Poniższy przykład ustawia te same właściwości w kodzie.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Tworzenie stylu kontrolki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia możliwość określania wyglądu hurtowników kontroli zamiast ustawiania właściwości dla każdego wystąpienia w aplikacji, tworząc <xref:System.Windows.Style>. Poniższy przykład tworzy obiekt <xref:System.Windows.Style> , który jest stosowany do każdego <xref:System.Windows.Controls.Button> w aplikacji. <xref:System.Windows.Style>definicje są zwykle zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.ResourceDictionary>w, <xref:System.Windows.FrameworkElement.Resources%2A> na przykład właściwości <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Można również zastosować styl tylko do niektórych formantów określonego typu przez przypisanie klucza do stylu i określenie tego klucza we `Style` właściwości formantu.  Aby uzyskać więcej informacji na temat stylów, zobacz [Style i tworzenia szablonów](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Tworzenie ControlTemplate  
 A <xref:System.Windows.Style> umożliwia ustawianie właściwości w wielu kontrolkach jednocześnie, ale czasami warto dostosować wygląd <xref:System.Windows.Controls.Control> poza tym, co <xref:System.Windows.Style>można zrobić, tworząc. Klasy dziedziczące z <xref:System.Windows.Controls.Control> klasy <xref:System.Windows.Controls.ControlTemplate>posiadają, która definiuje <xref:System.Windows.Controls.Control>strukturę i wygląd. Właściwość jest publiczna, <xref:System.Windows.Controls.Control> więc można nadać <xref:System.Windows.Controls.ControlTemplate> jej wartość inną niż domyślna. <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.Control.Template%2A> Można często określić nowy <xref:System.Windows.Controls.ControlTemplate> dla elementu <xref:System.Windows.Controls.Control> zamiast dziedziczyć z kontrolki, aby <xref:System.Windows.Controls.Control>dostosować wygląd.  
  
 Rozważmy bardzo powszechną kontrolę <xref:System.Windows.Controls.Button>.  Podstawowym zachowaniem <xref:System.Windows.Controls.Button> jest umożliwienie aplikacji podejmowania pewnych akcji, gdy użytkownik kliknie ją.  Domyślnie, <xref:System.Windows.Controls.Button> w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pojawia się jako podniesiony prostokąt.  Podczas tworzenia aplikacji możesz chcieć skorzystać z zachowania <xref:System.Windows.Controls.Button>typu--, czyli poprzez obsługę zdarzenia kliknięcia przycisku — ale można zmienić wygląd przycisku poza tym, co można zrobić, zmieniając właściwości przycisku.  W takim przypadku można utworzyć nowy <xref:System.Windows.Controls.ControlTemplate>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>dla.  <xref:System.Windows.Controls.ControlTemplate> Tworzyzzaokrąglonymirogami<xref:System.Windows.Controls.Button> i tłem gradientowym.  Zawiera <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.Border> , które <xref:System.Windows.Controls.Border.Background%2A> jest z<xref:System.Windows.Media.LinearGradientBrush> dwoma<xref:System.Windows.Media.GradientStop> obiektami.  Pierwsze <xref:System.Windows.Media.GradientStop> używa powiązania danych, <xref:System.Windows.Media.GradientStop> aby <xref:System.Windows.Media.GradientStop.Color%2A> powiązać właściwość z kolorem tła przycisku.  Po ustawieniu <xref:System.Windows.Controls.Control.Background%2A> właściwości <xref:System.Windows.Controls.Button>, kolor tej wartości będzie używany jako pierwszy <xref:System.Windows.Media.GradientStop>. Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md). W przykładzie tworzony jest również <xref:System.Windows.Trigger> obiekt, który zmienia wygląd <xref:System.Windows.Controls.Button> , gdy <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> jest `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Aby przykład działał prawidłowo <xref:System.Windows.Controls.Button> , <xref:System.Windows.Media.SolidColorBrush>Właściwośćmusi być ustawiona na wartość. <xref:System.Windows.Controls.Control.Background%2A>  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Możesz subskrybować zdarzenie kontrolki przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] albo kodu, ale możesz obsłużyć tylko zdarzenie w kodzie.  Poniższy przykład pokazuje, jak subskrybować `Click` zdarzenie. <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Poniższy przykład obsługuje `Click` zdarzenie <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Zawartość rozbudowana w kontrolkach  
 Większość klas, które dziedziczą <xref:System.Windows.Controls.Control> z klasy, ma pojemność do przechowywania zawartości rozbudowanej. Na przykład <xref:System.Windows.Controls.Label> może zawierać dowolny obiekt, taki jak ciąg <xref:System.Windows.Controls.Image>, a lub <xref:System.Windows.Controls.Panel>.  Poniższe klasy zapewniają obsługę bogatej zawartości i działają jako klasy bazowe dla większości kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Controls.ContentControl>--Przykłady klas, które dziedziczą z tej klasy <xref:System.Windows.Controls.Label>to, <xref:System.Windows.Controls.Button>, i. <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.ItemsControl>--Przykłady klas, które dziedziczą z tej klasy <xref:System.Windows.Controls.ListBox>to, <xref:System.Windows.Controls.Menu>, i. <xref:System.Windows.Controls.Primitives.StatusBar>  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--Przykłady klas, które dziedziczą z tej klasy <xref:System.Windows.Controls.TabItem>to, <xref:System.Windows.Controls.GroupBox>, i. <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Przykłady klas, które dziedziczą z tej klasy <xref:System.Windows.Controls.MenuItem>to, <xref:System.Windows.Controls.TreeViewItem>, i. <xref:System.Windows.Controls.ToolBar>  

 Aby uzyskać więcej informacji na temat tych klas bazowych, zobacz [WPF content model](wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Kontrolki według kategorii](controls-by-category.md)
- [Biblioteka kontrolek](control-library.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Dane wejściowe](../advanced/input-wpf.md)
- [Włączanie polecenia](../advanced/how-to-enable-a-command.md)
- [Przewodnik: Utwórz niestandardowy przycisk animowany](walkthroughs-create-a-custom-animated-button.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
