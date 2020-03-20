---
title: Kontrolki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2ec8c0a99f4e2431aed0d8c24168b7329de669f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187535"
---
# <a name="controls"></a>Kontrolki
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]jest dostarczanych z wieloma typowymi składnikami interfejsu użytkownika, <xref:System.Windows.Controls.Button>które <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBox>są <xref:System.Windows.Controls.Menu>używane w prawie każdej aplikacji systemu Windows, takich jak , , , i <xref:System.Windows.Controls.ListBox>. Historycznie te obiekty były określane jako formanty. Podczas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gdy SDK nadal używać terminu "control", aby luźno oznaczać dowolną klasę, która reprezentuje widoczny obiekt w aplikacji, należy <xref:System.Windows.Controls.Control> pamiętać, że klasa nie musi dziedziczyć z klasy, aby mieć widoczną obecność. Klasy, które <xref:System.Windows.Controls.Control> dziedziczą <xref:System.Windows.Controls.ControlTemplate>z klasy zawierają , co pozwala konsumentowi formantu radykalnie zmienić wygląd formantu bez konieczności tworzenia nowej podklasy.  W tym temacie omówiono, jak formanty (zarówno te, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, jak i te, które nie) są powszechnie używane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Tworzenie wystąpienia formantu  
 Formant można dodać do aplikacji za [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pomocą kodu.  W poniższym przykładzie pokazano, jak utworzyć prostą aplikację, która prosi użytkownika o ich imię i nazwisko.  W tym przykładzie utworzy się sześć formantów: [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dwie etykiety, dwa pola tekstowe i dwa przyciski w pliku . Wszystkie formanty mogą być tworzone w podobny sposób.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Poniższy przykład tworzy tę samą aplikację w kodzie. Dla zwięzłości, <xref:System.Windows.Controls.Grid> `grid1`utworzenie , został wykluczony z próbki. `grid1`ma te same definicje kolumn i wierszy, jak pokazano w poprzednim przykładzie. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Zmiana wyglądu formantu  
 Często zmienia się wygląd formantu, aby dopasować wygląd i działanie aplikacji. Wygląd formantu można zmienić, wykonując jedną z następujących czynności, w zależności od tego, co chcesz osiągnąć:  
  
- Zmień wartość właściwości formantu.  
  
- Utwórz <xref:System.Windows.Style> formantu.  
  
- Utwórz <xref:System.Windows.Controls.ControlTemplate> nowy dla formantu.  
  
### <a name="changing-a-controls-property-value"></a>Zmiana wartości właściwości formantu  
 Wiele formantów ma właściwości, które pozwalają zmienić <xref:System.Windows.Controls.Control.Background%2A> sposób, <xref:System.Windows.Controls.Button>w jaki formant się pojawia, takich jak . Można ustawić właściwości wartości w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obu i kod. W poniższym <xref:System.Windows.Controls.Control.Background%2A>przykładzie <xref:System.Windows.Controls.Control.FontSize%2A>ustawia , <xref:System.Windows.Controls.Button> i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Control.FontWeight%2A> właściwości na w .  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Poniższy przykład ustawia te same właściwości w kodzie.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Tworzenie stylu formantu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]daje możliwość określenia wyglądu kontroli hurtowych, zamiast ustawiania właściwości dla każdego wystąpienia w <xref:System.Windows.Style>aplikacji, tworząc program . Poniższy przykład <xref:System.Windows.Style> tworzy, który jest <xref:System.Windows.Controls.Button> stosowany do każdego w aplikacji. <xref:System.Windows.Style>definicje są zazwyczaj [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdefiniowane <xref:System.Windows.ResourceDictionary>w , <xref:System.Windows.FrameworkElement.Resources%2A> takich <xref:System.Windows.FrameworkElement>jak właściwość .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Styl można również zastosować tylko do niektórych formantów określonego typu, przypisując klucz `Style` do stylu i określając ten klucz we właściwości formantu.  Aby uzyskać więcej informacji o stylach, zobacz [Stylowanie i tworzenie szablonów](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Tworzenie panelu sterowania  
 A <xref:System.Windows.Style> umożliwia ustawienie właściwości na wielu formantach naraz, ale czasami można <xref:System.Windows.Controls.Control> dostosować wygląd poza to, <xref:System.Windows.Style>co można zrobić, tworząc program . Klasy, które <xref:System.Windows.Controls.Control> dziedziczą <xref:System.Windows.Controls.ControlTemplate>z klasy mają , który <xref:System.Windows.Controls.Control>definiuje strukturę i wygląd . Właściwość <xref:System.Windows.Controls.Control.Template%2A> a <xref:System.Windows.Controls.Control> jest publiczna, dzięki <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> czemu można podać, że jest inny niż jego domyślny. Często można określić <xref:System.Windows.Controls.ControlTemplate> nowy <xref:System.Windows.Controls.Control> dla zamiast dziedziczenia z formantu, <xref:System.Windows.Controls.Control>aby dostosować wygląd .  
  
 Rozważmy bardzo wspólną kontrolę, <xref:System.Windows.Controls.Button>.  Podstawowym zachowaniem <xref:System.Windows.Controls.Button> jest umożliwienie aplikacji do podjęcia pewnych działań, gdy użytkownik kliknie go.  Domyślnie <xref:System.Windows.Controls.Button> in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest wyświetlany jako podniesiony prostokąt.  Podczas tworzenia aplikacji, można skorzystać z zachowania <xref:System.Windows.Controls.Button>--oznacza, że obsługi przycisku kliknij zdarzenia - ale można zmienić wygląd przycisku poza to, co można zrobić, zmieniając właściwości przycisku.  W takim przypadku można utworzyć <xref:System.Windows.Controls.ControlTemplate>nowy program .  
  
 Poniższy przykład <xref:System.Windows.Controls.ControlTemplate> tworzy <xref:System.Windows.Controls.Button>fora .  Tworzy <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.Button> zaokrąglonymi narożnikami i tłem gradientu.  Zawiera, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Border> którego <xref:System.Windows.Controls.Border.Background%2A> jest <xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.GradientStop> z dwoma obiektami.  Pierwszy <xref:System.Windows.Media.GradientStop> używa powiązania danych do <xref:System.Windows.Media.GradientStop.Color%2A> powiązania <xref:System.Windows.Media.GradientStop> właściwości do koloru tła przycisku.  Po ustawieniu <xref:System.Windows.Controls.Control.Background%2A> właściwości <xref:System.Windows.Controls.Button>, kolor tej wartości będzie używany <xref:System.Windows.Media.GradientStop>jako pierwszy . Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md). W <xref:System.Windows.Trigger> przykładzie tworzy również, który <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> zmienia `true`wygląd, gdy jest .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Właściwość <xref:System.Windows.Controls.Control.Background%2A> musi <xref:System.Windows.Controls.Button> być ustawiona <xref:System.Windows.Media.SolidColorBrush> na przykład, aby działał poprawnie.  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Subskrybowanie wydarzeń  
 Możesz subskrybować zdarzenie formantu przy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] użyciu kodu lub kodu, ale można obsługiwać zdarzenie tylko w kodzie.  W poniższym przykładzie pokazano, `Click` jak subskrybować zdarzenie <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Poniższy przykład obsługuje `Click` zdarzenie <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Bogata zawartość w formancie  
 Większość klas, które <xref:System.Windows.Controls.Control> dziedziczą z klasy mają zdolność do zawierają zawartość rozszerzoną. Na przykład <xref:System.Windows.Controls.Label> może zawierać dowolny obiekt, taki <xref:System.Windows.Controls.Image>jak ciąg, znak , lub . <xref:System.Windows.Controls.Panel>  Następujące klasy zapewniają obsługę zawartości rozszerzonej i działają jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]klasy podstawowe dla większości formantów w .  
  
- <xref:System.Windows.Controls.ContentControl>-- Niektóre przykłady klas, które <xref:System.Windows.Controls.Label>dziedziczą z tej klasy są , <xref:System.Windows.Controls.Button>i <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>-- Niektóre przykłady klas, które <xref:System.Windows.Controls.ListBox>dziedziczą z tej klasy są , <xref:System.Windows.Controls.Menu>i <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- Niektóre przykłady klas, które <xref:System.Windows.Controls.TabItem>dziedziczą z tej klasy są , <xref:System.Windows.Controls.GroupBox>i <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Niektóre przykłady klas, które dziedziczą <xref:System.Windows.Controls.TreeViewItem>z <xref:System.Windows.Controls.ToolBar>tej klasy są <xref:System.Windows.Controls.MenuItem>, i .  

 Aby uzyskać więcej informacji na temat tych klas podstawowych, zobacz [Model zawartości WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Kontrolki według kategorii](controls-by-category.md)
- [Biblioteka formantów](control-library.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Przegląd Wiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Wejście](../advanced/input-wpf.md)
- [Włączanie polecenia](../advanced/how-to-enable-a-command.md)
- [Przewodnik: tworzenie niestandardowego przycisku animowanego](walkthroughs-create-a-custom-animated-button.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
