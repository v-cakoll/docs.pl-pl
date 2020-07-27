---
title: Formanty
description: Dowiedz się więcej na temat Windows Presentation Foundation wspólnych składników interfejsu użytkownika, nazywanych kontrolkami, ale które mogą nie dziedziczyć z klasy formantów.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: c3d9d3a38cf5f84e21df195e113e264e5a4ac025
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165849"
---
# <a name="controls"></a>Formanty
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]dostarcza wiele typowych składników interfejsu użytkownika, które są używane w prawie każdej aplikacji systemu Windows, takiej jak <xref:System.Windows.Controls.Button> ,,, <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu> i <xref:System.Windows.Controls.ListBox> . Historycznie te obiekty zostały określone jako kontrolki. Mimo że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestaw SDK kontynuuje używanie terminu "kontrola" do swobodnego oznaczania każdej klasy, która reprezentuje widoczny obiekt w aplikacji, należy zauważyć, że Klasa nie musi dziedziczyć z <xref:System.Windows.Controls.Control> klasy, aby mieć widoczną obecność. Klasy dziedziczące z <xref:System.Windows.Controls.Control> klasy zawierają element <xref:System.Windows.Controls.ControlTemplate> , który umożliwia konsumentowi kontrolce radykalnie Zmienianie wyglądu kontrolki bez konieczności tworzenia nowej podklasy.  W tym temacie omówiono sposób, w jaki formanty (zarówno te, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, jak i te, które nie są) są często używane w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Tworzenie wystąpienia kontrolki  
 Możesz dodać formant do aplikacji przy użyciu albo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu.  Poniższy przykład pokazuje, jak utworzyć prostą aplikację, która monituje użytkownika o podanie ich imienia i nazwiska.  Ten przykład tworzy sześć kontrolek: dwie etykiety, dwa pola tekstowe i dwa przyciski w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Wszystkie kontrolki można tworzyć podobnie.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 W poniższym przykładzie jest tworzona ta sama aplikacja w kodzie. W przypadku zwięzłości Tworzenie elementu <xref:System.Windows.Controls.Grid> , `grid1` zostało wyłączone z przykładu. `grid1`zawiera te same definicje kolumn i wierszy, jak pokazano w powyższym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykładzie.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Zmiana wyglądu kontrolki  
 Typowym sposobem zmiany wyglądu kontrolki jest dopasowanie wyglądu i sposobu działania aplikacji. Wygląd formantu można zmienić, wykonując jedną z następujących czynności, w zależności od tego, co chcesz osiągnąć:  
  
- Zmień wartość właściwości formantu.  
  
- Utwórz <xref:System.Windows.Style> dla kontrolki.  
  
- Utwórz nową <xref:System.Windows.Controls.ControlTemplate> kontrolkę.  
  
### <a name="changing-a-controls-property-value"></a>Zmiana wartości właściwości kontrolki  
 Wiele kontrolek ma właściwości, które umożliwiają zmianę sposobu wyświetlania kontrolki, na przykład <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.Controls.Button> . Można ustawić właściwości wartości w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kodzie. Poniższy przykład ustawia <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.FontSize%2A> właściwości,, i w <xref:System.Windows.Controls.Control.FontWeight%2A> <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Poniższy przykład ustawia te same właściwości w kodzie.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Tworzenie stylu kontrolki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia możliwość określania wyglądu hurtowników kontroli zamiast ustawiania właściwości dla każdego wystąpienia w aplikacji, tworząc <xref:System.Windows.Style> . Poniższy przykład tworzy obiekt <xref:System.Windows.Style> , który jest stosowany do każdego <xref:System.Windows.Controls.Button> w aplikacji. <xref:System.Windows.Style>definicje są zwykle zdefiniowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w, na przykład <xref:System.Windows.ResourceDictionary> <xref:System.Windows.FrameworkElement.Resources%2A> właściwości <xref:System.Windows.FrameworkElement> .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Można również zastosować styl tylko do niektórych formantów określonego typu przez przypisanie klucza do stylu i określenie tego klucza we `Style` właściwości formantu.  Aby uzyskać więcej informacji na temat stylów, zobacz [Style i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
### <a name="creating-a-controltemplate"></a>Tworzenie ControlTemplate  
 A <xref:System.Windows.Style> umożliwia ustawianie właściwości w wielu kontrolkach jednocześnie, ale czasami warto dostosować wygląd poza tym, <xref:System.Windows.Controls.Control> co można zrobić, tworząc <xref:System.Windows.Style> . Klasy dziedziczące z <xref:System.Windows.Controls.Control> klasy posiadają <xref:System.Windows.Controls.ControlTemplate> , która definiuje strukturę i wygląd <xref:System.Windows.Controls.Control> . <xref:System.Windows.Controls.Control.Template%2A>Właściwość <xref:System.Windows.Controls.Control> jest publiczna, więc można nadać jej wartość <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> inną niż domyślna. Można często określić nowy <xref:System.Windows.Controls.ControlTemplate> dla elementu <xref:System.Windows.Controls.Control> zamiast dziedziczyć z kontrolki, aby dostosować wygląd <xref:System.Windows.Controls.Control> .  
  
 Rozważmy bardzo powszechną kontrolę <xref:System.Windows.Controls.Button> .  Podstawowym zachowaniem <xref:System.Windows.Controls.Button> jest umożliwienie aplikacji podejmowania pewnych akcji, gdy użytkownik kliknie ją.  Domyślnie, <xref:System.Windows.Controls.Button> w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pojawia się jako podniesiony prostokąt.  Podczas tworzenia aplikacji możesz chcieć skorzystać z zachowania typu <xref:System.Windows.Controls.Button> --, czyli poprzez obsługę zdarzenia kliknięcia przycisku — ale można zmienić wygląd przycisku poza tym, co można zrobić, zmieniając właściwości przycisku.  W takim przypadku można utworzyć nowy <xref:System.Windows.Controls.ControlTemplate> .  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> .  <xref:System.Windows.Controls.ControlTemplate>Tworzy <xref:System.Windows.Controls.Button> z zaokrąglonymi rogami i tłem gradientowym.  <xref:System.Windows.Controls.ControlTemplate>Zawiera a, <xref:System.Windows.Controls.Border> które <xref:System.Windows.Controls.Border.Background%2A> jest <xref:System.Windows.Media.LinearGradientBrush> z dwoma <xref:System.Windows.Media.GradientStop> obiektami.  Pierwsze <xref:System.Windows.Media.GradientStop> używa powiązania danych, aby powiązać <xref:System.Windows.Media.GradientStop.Color%2A> Właściwość z <xref:System.Windows.Media.GradientStop> kolorem tła przycisku.  Po ustawieniu <xref:System.Windows.Controls.Control.Background%2A> właściwości <xref:System.Windows.Controls.Button> , kolor tej wartości będzie używany jako pierwszy <xref:System.Windows.Media.GradientStop> . Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md). W przykładzie tworzony jest również obiekt <xref:System.Windows.Trigger> , który zmienia wygląd, <xref:System.Windows.Controls.Button> gdy <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> jest `true` .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Aby <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> przykład działał prawidłowo, właściwość musi być ustawiona na wartość <xref:System.Windows.Media.SolidColorBrush> .  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Możesz subskrybować zdarzenie kontrolki przy użyciu albo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodu, ale możesz obsłużyć tylko zdarzenie w kodzie.  Poniższy przykład pokazuje, jak subskrybować `Click` zdarzenie <xref:System.Windows.Controls.Button> .  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Poniższy przykład obsługuje `Click` zdarzenie <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Zawartość rozbudowana w kontrolkach  
 Większość klas, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, ma pojemność do przechowywania zawartości rozbudowanej. Na przykład <xref:System.Windows.Controls.Label> może zawierać dowolny obiekt, taki jak ciąg, a <xref:System.Windows.Controls.Image> lub <xref:System.Windows.Controls.Panel> .  Poniższe klasy zapewniają obsługę bogatej zawartości i działają jako klasy bazowe dla większości kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
- <xref:System.Windows.Controls.ContentControl>--Przykłady klas, które dziedziczą z tej klasy to <xref:System.Windows.Controls.Label> , <xref:System.Windows.Controls.Button> , i <xref:System.Windows.Controls.ToolTip> .  
  
- <xref:System.Windows.Controls.ItemsControl>--Przykłady klas, które dziedziczą z tej klasy to <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.Menu> , i <xref:System.Windows.Controls.Primitives.StatusBar> .  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--Przykłady klas, które dziedziczą z tej klasy to <xref:System.Windows.Controls.TabItem> , <xref:System.Windows.Controls.GroupBox> , i <xref:System.Windows.Controls.Expander> .  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Przykłady klas, które dziedziczą z tej klasy to <xref:System.Windows.Controls.MenuItem> , <xref:System.Windows.Controls.TreeViewItem> , i <xref:System.Windows.Controls.ToolBar> .  

 Aby uzyskać więcej informacji na temat tych klas bazowych, zobacz [WPF content model](wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Kontrolki według kategorii](controls-by-category.md)
- [Biblioteka formantów](control-library.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Dane wejściowe](../advanced/input-wpf.md)
- [Włączanie polecenia](../advanced/how-to-enable-a-command.md)
- [Przewodniki: Tworzenie niestandardowego przycisku animowanego](walkthroughs-create-a-custom-animated-button.md)
- [Niestandardowe dostosowywanie formantu](control-customization.md)
