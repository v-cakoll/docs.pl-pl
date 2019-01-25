---
title: Formanty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 83f044f403fe6d4d9c77c5b4d2045d58b50b97a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700666"
---
# <a name="controls"></a>Formanty
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest dostarczany z wiele wspólnych składników interfejsu użytkownika, które są używane w prawie każdym aplikacji Windows, takich jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.ListBox>. W przeszłości te obiekty mają zostały nazywane kontrolki. Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawu SDK w dalszym ciągu używany jest termin "control" luźno oznacza każdej klasy, który reprezentuje obiekt widoczne w aplikacji, ważne jest, aby należy zauważyć, że klasa nie dziedziczy po <xref:System.Windows.Controls.Control> klasy jest obecna widoczne. Klasy, które dziedziczą z <xref:System.Windows.Controls.Control> klasa zawiera <xref:System.Windows.Controls.ControlTemplate>, co umożliwia konsumentowi radykalnie zmienić wygląd kontrolki bez konieczności tworzenia nowej podklasy kontrolki.  W tym temacie omówiono sposób kontrolki (zarówno te, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, które nie obsługują) są powszechnie używane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Utworzenie wystąpienia kontrolki  
 Można dodać kontrolki do aplikacji przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu.  Poniższy przykład pokazuje, jak utworzyć prostą aplikację, która prosi użytkownika o swoje imię i nazwisko.  W tym przykładzie tworzy sześć kontrolki: dwóch etykiet dwóch pól tekstowych i dwa przyciski w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podobnie można utworzyć wszystkich kontrolek.  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Poniższy przykład tworzy tej samej aplikacji w kodzie. Celu skrócenia programu, tworzenia <xref:System.Windows.Controls.Grid>, `grid1`, został wykluczony z próbki. `grid1` ma te same definicje kolumn i wierszy, jak pokazano w poprzednim [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Zmienianie wyglądu formantu  
 Są często zmieniać wygląd kontrolki, aby dopasować wygląd i działanie aplikacji. Możesz zmienić wygląd formantu, wykonując jedną z poniższych pozycji w zależności od tego, co chcesz osiągnąć:  
  
-   Zmień wartość właściwości formantu.  
  
-   Utwórz <xref:System.Windows.Style> dla formantu.  
  
-   Utwórz nową <xref:System.Windows.Controls.ControlTemplate> dla formantu.  
  
### <a name="changing-a-controls-property-value"></a>Zmiana wartości właściwości kontrolki  
 Wiele kontrolki mają właściwości, które pozwalają zmienić sposób wyświetlania kontrolki, takie jak <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Można ustawić właściwości wartość w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod. Poniższy przykład ustawia <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontWeight%2A> właściwości <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 W poniższym przykładzie ustawiono te same właściwości w kodzie.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Tworzenie stylu dla formantu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia możliwość określenia wygląd formantów hurtowym, zamiast ustawiać właściwości w każdym wystąpieniu w aplikacji, tworząc <xref:System.Windows.Style>. Poniższy przykład tworzy <xref:System.Windows.Style> mający zastosowanie do każdego <xref:System.Windows.Controls.Button> w aplikacji. <xref:System.Windows.Style> definicje są zazwyczaj definiowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w <xref:System.Windows.ResourceDictionary>, takich jak <xref:System.Windows.FrameworkElement.Resources%2A> właściwość <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Można również zastosować styl do określonych formantów określonego typu, przypisując klucz stylu i określający tego klucza w `Style` właściwości formantu.  Aby uzyskać więcej informacji na temat style zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Tworzenie ControlTemplate  
 A <xref:System.Windows.Style> można ustawić właściwości dla kilku formantów w czasie, ale czasami możesz chcieć dostosować wygląd <xref:System.Windows.Controls.Control> poza co można zrobić, tworząc <xref:System.Windows.Style>. Klasy, które dziedziczą z <xref:System.Windows.Controls.Control> klasa ma <xref:System.Windows.Controls.ControlTemplate>, który definiuje strukturę i wygląd <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Właściwość <xref:System.Windows.Controls.Control> jest publiczna, dzięki czemu możesz nadać <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> który jest inny niż domyślny. Często można określić nowy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Control> zamiast dziedziczenie z kontrolki, aby dostosować wygląd <xref:System.Windows.Controls.Control>.  
  
 Należy wziąć pod uwagę bardzo często kontrola i <xref:System.Windows.Controls.Button>.  Podstawowe zachowanie <xref:System.Windows.Controls.Button> jest umożliwienie aplikacji wykonania określonego działania, gdy użytkownik kliknie przycisk.  Domyślnie <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] postać wpuszczonych prostokąta.  Podczas tworzenia aplikacji, możesz chcieć skorzystać z zachowaniem <xref:System.Windows.Controls.Button>— oznacza, że obsługa przycisk kliknij zdarzenie —, ale można zmienić wygląd poza co można zrobić, zmieniając właściwości przycisku.  W takim przypadku można utworzyć nowego <xref:System.Windows.Controls.ControlTemplate>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> Tworzy <xref:System.Windows.Controls.Button> zaokrąglone rogi i gradientu tła.  <xref:System.Windows.Controls.ControlTemplate> Zawiera <xref:System.Windows.Controls.Border> którego <xref:System.Windows.Controls.Border.Background%2A> jest <xref:System.Windows.Media.LinearGradientBrush> przy użyciu dwóch <xref:System.Windows.Media.GradientStop> obiektów.  Pierwszy <xref:System.Windows.Media.GradientStop> używa powiązanie danych do powiązania <xref:System.Windows.Media.GradientStop.Color%2A> właściwość <xref:System.Windows.Media.GradientStop> na kolor tła przycisku.  Po ustawieniu <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.Button>, kolor ta wartość będzie służyć jako pierwszy <xref:System.Windows.Media.GradientStop>. Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md). W przykładzie jest tworzony również <xref:System.Windows.Trigger> zmienia się wygląd <xref:System.Windows.Controls.Button> podczas <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> jest `true`.  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A> Właściwość <xref:System.Windows.Controls.Button> musi być równa <xref:System.Windows.Media.SolidColorBrush> na przykład zapewnić prawidłowe działanie.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Można subskrybować zdarzenie kontroli przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kod, ale może obsługiwać tylko zdarzenia w kodzie.  Poniższy przykład pokazuje sposób subskrybowania `Click` zdarzenia <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Następujące uchwyty przykład `Click` zdarzenia <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Sformatowana zawartość w formantach  
 Większość klas, które dziedziczą z <xref:System.Windows.Controls.Control> klasa ma pojemność, aby pomieścić sformatowanej zawartości. Na przykład <xref:System.Windows.Controls.Label> może zawierać dowolnego obiektu, na przykład ciąg, <xref:System.Windows.Controls.Image>, lub <xref:System.Windows.Controls.Panel>.  Następujące klasy obsługuje bogatą zawartość i działa jako klay bazowe dla większości kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>--Kilka przykładów klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, i <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>--Kilka przykładów klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>--Kilka przykładów klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, i <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>--Kilka przykładów klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, i <xref:System.Windows.Controls.ToolBar>.  

  
 Aby uzyskać więcej informacji na temat tych klas bazowych, zobacz [Model zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Kontrolki według kategorii](../../../../docs/framework/wpf/controls/controls-by-category.md)
- [Biblioteka kontrolek](../../../../docs/framework/wpf/controls/control-library.md)
- [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Dane wejściowe](../../../../docs/framework/wpf/advanced/input-wpf.md)
- [Włączanie polecenia](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)
- [Przewodnik: Tworzenie niestandardowego przycisku animowanego](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)
- [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)
