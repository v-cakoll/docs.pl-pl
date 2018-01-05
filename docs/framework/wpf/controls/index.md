---
title: Formanty
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66c6cc58423a2af8d0fd6de93b8884918888fb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="controls"></a>Formanty
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]jest dostarczany z wielu typowych składników interfejsu użytkownika, które są używane w większości aplikacji systemu Windows, takich jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.ListBox>. W przeszłości te obiekty mają zostały określone jako formantów. Gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawu SDK w dalszym ciągu używa termin "control" słabo oznacza wszystkie klasy, która reprezentuje obiekt widoczne w aplikacji, ważne jest, aby należy zauważyć, że klasa nie dziedziczy po <xref:System.Windows.Controls.Control> klasy mają obecności widoczne. Klasy, które dziedziczą z <xref:System.Windows.Controls.Control> klasa zawiera <xref:System.Windows.Controls.ControlTemplate>, dzięki czemu konsumenta formantu znacząco zmienić wygląd formantu, bez konieczności tworzenia nową podklasę.  W tym temacie omówiono sposób formantów (zarówno te, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, które nie) są często używane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Tworzenie wystąpienia formantu  
 Można dodać formantu do aplikacji przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu.  Poniższy przykład przedstawia sposób tworzenia prostej aplikacji, w którym wprowadza swoje imię i nazwisko użytkownika.  W tym przykładzie jest tworzony sześciu kontrolki: dwie etykiety dwa pola tekstowe i dwóch przycisków w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podobnie można utworzyć wszystkie formanty.  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Poniższy przykład tworzy tej samej aplikacji w kodzie. Jednak tworzenie <xref:System.Windows.Controls.Grid>, `grid1`, został on wykluczony z próbki. `grid1`ma takie same definicje kolumn i wierszy, jak pokazano w poprzednim [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Zmienianie wyglądu formantu  
 Są często, aby zmienić wygląd formantu, aby dopasować wygląd i działanie aplikacji. Można zmienić wygląd formantu, wykonując jedną z następujących czynności, w zależności od tego, co chcesz zrobić:  
  
-   Zmień wartość właściwości formantu.  
  
-   Utwórz <xref:System.Windows.Style> dla formantu.  
  
-   Utwórz nową <xref:System.Windows.Controls.ControlTemplate> dla formantu.  
  
### <a name="changing-a-controls-property-value"></a>Zmiana wartości właściwości formantu  
 Wiele formantów mają właściwości, które pozwala zmienić sposób wyświetlania kontrolki, takich jak <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Można ustawić właściwości wartości w obu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i kod. W poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontWeight%2A> właściwości <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Poniższy przykład ustawia takie same właściwości w kodzie.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Tworzenie stylu dla formantu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umożliwi to przywrócenie, aby określić wygląd formantów hurtowym, zamiast właściwości na każde wystąpienie w aplikacji, tworząc <xref:System.Windows.Style>. Poniższy przykład tworzy <xref:System.Windows.Style> do każdej zastosowano <xref:System.Windows.Controls.Button> w aplikacji. <xref:System.Windows.Style>definicje są zazwyczaj definiowane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w <xref:System.Windows.ResourceDictionary>, takich jak <xref:System.Windows.FrameworkElement.Resources%2A> właściwość <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Styl można zastosować do określonego typu niektórych formantów, przypisując klucz styl i określania tego klucza w `Style` właściwości formantu.  Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Tworzenie ControlTemplate  
 A <xref:System.Windows.Style> umożliwia ustawienie właściwości na wielu formantów w czasie, ale czasami może być dostosowanie wyglądu <xref:System.Windows.Controls.Control> poza co można zrobić, tworząc <xref:System.Windows.Style>. Klasy, które dziedziczą z <xref:System.Windows.Controls.Control> klasa ma <xref:System.Windows.Controls.ControlTemplate>, który definiuje strukturę i wygląd <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Właściwość <xref:System.Windows.Controls.Control> jest publiczny, aby zapewnić <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> który jest inny niż domyślny. Często można określić nową <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Control> zamiast dziedziczenie z formantu, aby dostosować wygląd <xref:System.Windows.Controls.Control>.  
  
 Należy wziąć pod uwagę bardzo powszechne formantu <xref:System.Windows.Controls.Button>.  Podstawowe zachowanie <xref:System.Windows.Controls.Button> jest umożliwienie aplikacji to podjąć akcję po kliknięciu przez użytkownika.  Domyślnie <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] postać zgłoszono prostokąta.  Podczas tworzenia aplikacji, można skorzystać z zachowaniem <xref:System.Windows.Controls.Button>--oznacza to, że obsługa Zdarzenie — kliknięcia przycisku, ale można zmienić wygląd przycisku poza co można zrobić, zmieniając właściwości przycisku.  W takim przypadku można utworzyć nowy <xref:System.Windows.Controls.ControlTemplate>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> Tworzy <xref:System.Windows.Controls.Button> zaokrąglone narożniki i gradientu tła.  <xref:System.Windows.Controls.ControlTemplate> Zawiera <xref:System.Windows.Controls.Border> których <xref:System.Windows.Controls.Border.Background%2A> jest <xref:System.Windows.Media.LinearGradientBrush> z dwoma <xref:System.Windows.Media.GradientStop> obiektów.  Pierwszy <xref:System.Windows.Media.GradientStop> wykorzystuje wiązania danych do powiązania <xref:System.Windows.Media.GradientStop.Color%2A> właściwość <xref:System.Windows.Media.GradientStop> na kolor tła przycisku.  Podczas ustawiania <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.Button>, kolor tej wartości będą używane jako pierwszy <xref:System.Windows.Media.GradientStop>. Aby uzyskać więcej informacji na temat wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md). W przykładzie jest tworzony także <xref:System.Windows.Trigger> który zmienia wygląd <xref:System.Windows.Controls.Button> podczas <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> jest `true`.  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A> Właściwość <xref:System.Windows.Controls.Button> musi mieć ustawioną <xref:System.Windows.Media.SolidColorBrush> na przykład aby działać poprawnie.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń  
 Będzie możliwe subskrybowanie zdarzeń formantu przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kod, ale może obsługiwać tylko zdarzenia w kodzie.  Poniższy przykład przedstawia sposób subskrybowania `Click` zdarzenie <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Następujący przykład uchwytów `Click` zdarzenie <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Zawartość sformatowana w formantach  
 Większość klas, które dziedziczą z <xref:System.Windows.Controls.Control> klasa ma zdolność do sformatowanego zawartością. Na przykład <xref:System.Windows.Controls.Label> może zawierać dowolnego obiektu, takiego jak ciąg, <xref:System.Windows.Controls.Image>, lub <xref:System.Windows.Controls.Panel>.  Następujące klasy obsługuje bogatej zawartości i działania jako klasy podstawowe dla większości formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>--Przykłady klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, i <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>--Przykłady klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>--Przykłady klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, i <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>--Przykłady klas, które dziedziczą z tej klasy są <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, i <xref:System.Windows.Controls.ToolBar>.  
  
-  
  
 Aby uzyskać więcej informacji na temat tych klas podstawowych, zobacz [modelu zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Kontrolki według kategorii](../../../../docs/framework/wpf/controls/controls-by-category.md)  
 [Biblioteka kontrolek](../../../../docs/framework/wpf/controls/control-library.md)  
 [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Dane wejściowe](../../../../docs/framework/wpf/advanced/input-wpf.md)  
 [Włączanie polecenia](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)  
 [Przewodnik: tworzenie niestandardowego przycisku animowanego](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)
