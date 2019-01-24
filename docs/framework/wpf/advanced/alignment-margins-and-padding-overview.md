---
title: Przegląd Wyrównanie, marginesy i wypełnienia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: 5c716c07fabe5b93f13c86f8d347e4fd4d058145
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569957"
---
# <a name="alignment-margins-and-padding-overview"></a>Przegląd Wyrównanie, marginesy i wypełnienia
<xref:System.Windows.FrameworkElement> Klasa udostępnia kilka właściwości, które są używane do dokładnie pozycjonować elementy podrzędne. W tym temacie omówiono cztery najważniejsze właściwości: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Efekty te właściwości są ważne, aby dowiedzieć się, ponieważ stanowią podstawę do kontrolowania położenie elementów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Wprowadzenie do pozycjonowania elementu  
 Wiele sposobów, aby ustalić położenie elementów za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jednak osiągnięcia idealny układ wykracza poza po prostu wybierając po prawej stronie <xref:System.Windows.Controls.Panel> elementu. Precyzyjnego pozycjonowania wymaga zrozumienia <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości.  
  
 Poniższa ilustracja przedstawia scenariusz układ, który wykorzystuje kilka właściwości pozycjonowania.  
  
 ![WPF, na przykład właściwości pozycjonowania](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na pierwszy rzut oka <xref:System.Windows.Controls.Button> elementy na tej ilustracji może pojawić się na umieszczenie losowo. Jednak ich pozycje faktycznie dokładnie są kontrolowane przez przy użyciu kombinacji marginesy, wyrównanie i dopełnienia.  
  
 Poniższy przykład zawiera opis sposobu tworzenia układu na poprzedniej ilustracji. A <xref:System.Windows.Controls.Border> element hermetyzuje nadrzędnego <xref:System.Windows.Controls.StackPanel>, za pomocą <xref:System.Windows.Controls.Border.Padding%2A> wynoszącej 15 pikselach niezależnych od urządzenia. Jest to przyczyną wąskiego <xref:System.Windows.Media.Brushes.LightBlue%2A> zespół, który otacza podrzędne <xref:System.Windows.Controls.StackPanel>. Elementy podrzędne <xref:System.Windows.Controls.StackPanel> są używane w celu przedstawienia wszystkich różne właściwości pozycjonowania, które zostały szczegółowo opisane w tym temacie. Trzy <xref:System.Windows.Controls.Button> elementy są używane w celu zademonstrowania zarówno <xref:System.Windows.FrameworkElement.Margin%2A> i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Na poniższym diagramie przedstawiono dokładniejszy widok różne właściwości pozycjonowania, które są używane w poprzednim przykładzie. Kolejne sekcje w tym temacie opisano szczegółowo sposób użycia każdej właściwości pozycjonowania.  
  
 ![Właściwości pozycjonowania z ekranu wywołać&#45;szczegółowymi informacjami dotyczącymi](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Opis właściwości wyrównania  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości opisują położenie elementu podrzędnego w obrębie elementu nadrzędnego układu przydzielonego miejsca. Korzystając z tych właściwości ze sobą, należy dokładnie pozycjonować elementy podrzędne. Na przykład, elementy podrzędne <xref:System.Windows.Controls.DockPanel> można określić cztery różne poziomy wyrównanie: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, lub <xref:System.Windows.HorizontalAlignment.Center>, lub <xref:System.Windows.HorizontalAlignment.Stretch> celu wypełnienia dostępnego miejsca. Podobne wartości są dostępne dla rozmieszczenie w pionie.  
  
> [!NOTE]
>  Jawnie ustaw <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości w elemencie pierwszeństwo <xref:System.Windows.HorizontalAlignment.Stretch> wartości właściwości. Trwa próba skonfigurowania <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość `Stretch` skutkuje `Stretch` żądania są ignorowane.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>Właściwość HorizontalAlignment  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Właściwości deklaruje charakterystyki wyrównania poziomego do zastosowania do elementów podrzędnych. W poniższej tabeli przedstawiono listę możliwych wartości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Elementy podrzędne są wyrównane do lewej miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Elementy podrzędne są wyrównane do środka miejsce przydzielone układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Elementy podrzędne są wyrównane z prawej strony elementu nadrzędnego układu przydzielonego miejsca.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Ustawienie domyślne)|Elementy podrzędne są rozciągnięte do wypełnienia elementu nadrzędnego układu przydzielonego miejsca. Jawne <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości mają pierwszeństwo.|  
  
 Poniższy przykład pokazuje, jak zastosować <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwość <xref:System.Windows.Controls.Button> elementów. Każda wartość atrybutu jest wyświetlany, aby lepiej zilustrować różnych zachowań renderowania.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Powyższy kod daje układ podobny do poniższej ilustracji. Pozycjonowania skutki <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Właściwości HorizontalAlignment](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>Właściwość VerticalAlignment  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Właściwości w tym artykule opisano charakterystyki wyrównania poziomego do zastosowania do elementów podrzędnych. W poniższej tabeli przedstawiono listę możliwych wartości dla <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Elementy podrzędne są wyrównane do górnej części miejsce przydzielone układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Center>|Elementy podrzędne są wyrównane do środka miejsce przydzielone układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Elementy podrzędne są wyrównane do dolnej części elementu nadrzędnego układu przydzielonego miejsca.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Ustawienie domyślne)|Elementy podrzędne są rozciągnięte do wypełnienia elementu nadrzędnego układu przydzielonego miejsca. Jawne <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości mają pierwszeństwo.|  
  
 Poniższy przykład pokazuje, jak zastosować <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwość <xref:System.Windows.Controls.Button> elementów. Każda wartość atrybutu jest wyświetlany, aby lepiej zilustrować różnych zachowań renderowania. Do celów tego przykładu <xref:System.Windows.Controls.Grid> element z liniami siatki widoczny jest używany jako element nadrzędny, aby lepiej zilustrować zachowanie układ każdej wartości właściwości.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Powyższy kod daje układ podobny do poniższej ilustracji. Pozycjonowania skutki <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Właściwości VerticalAlignment](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Opis właściwości marginesów  
 <xref:System.Windows.FrameworkElement.Margin%2A> Właściwość opisuje odległość między elementem i jego podrzędne lub elementów równorzędnych. <xref:System.Windows.FrameworkElement.Margin%2A> Możliwe wartości to jednolite, przy użyciu składni `Margin="20"`. Przy użyciu tej składni jednolitego <xref:System.Windows.FrameworkElement.Margin%2A> 20 urządzenia pikselach niezależnych od mają zostać zastosowane do elementu. <xref:System.Windows.FrameworkElement.Margin%2A> wartości można również mieć postać cztery różne wartości, każda wartość opisujących różne margines dotyczą po lewej stronie, górnej, prawej strony i dolnej (w tej kolejności), takich jak `Margin="0,10,5,25"`. Właściwe stosowanie <xref:System.Windows.FrameworkElement.Margin%2A> właściwość umożliwia bardzo precyzyjnego miejsce renderowania elementu i miejsce renderowania elementów sąsiadujących i elementy podrzędne.  
  
> [!NOTE]
>  Margines niezerową stosuje miejsca poza elementem <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Poniższy przykład pokazuje, jak zastosować jednolitego marginesy wokół grupy <xref:System.Windows.Controls.Button> elementów. <xref:System.Windows.Controls.Button> Elementy są równomiernie rozłożone buforem margines dziesięciu piksel w każdym kierunku.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 W wielu przypadkach jednolitego margines nie jest właściwe. W takich przypadkach można zastosować obsługuje technologię niejednolitego odstępy. Poniższy przykład przedstawia sposób stosowania odstęp margines obsługuje technologię niejednolitego do elementów podrzędnych. Marginesy są opisane w następującej kolejności: do lewej, top, kliknij prawym przyciskiem myszy, dół.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Opis właściwości dopełnienie  
 Dopełnienie przypomina <xref:System.Windows.FrameworkElement.Margin%2A> pod względem większości. Właściwość dopełnienie jest uwidaczniany w tylko na kilka klas, przede wszystkim jako udogodnienie: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, i <xref:System.Windows.Controls.TextBlock> przykładów klas, które udostępniają właściwość dopełnienia. <xref:System.Windows.Controls.Border.Padding%2A> Właściwość powiększa skuteczne rozmiar elementu podrzędnego przez określony <xref:System.Windows.Thickness> wartość.  
  
 Poniższy przykład pokazuje, jak zastosować <xref:System.Windows.Controls.Border.Padding%2A> do elementu nadrzędnego <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Za pomocą wyrównanie, marginesy i dopełnienie w aplikacji  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> zapewniają kontrolę nad pozycjonowania niezbędne do utworzenia złożony [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Skutki każdej właściwości służy do zmiany elementu podrzędnego pozycjonowanie, co pozwala elastyczność w tworzeniu dynamicznych aplikacji i środowisk pracy użytkownika.  
  
 W poniższym przykładzie pokazano każdego pojęcia, które zostały szczegółowo opisane w tym temacie. Opierając się na infrastrukturę, znaleziono w pierwszym przykładzie w tym temacie, ten przykład dodaje <xref:System.Windows.Controls.Grid> element jako element podrzędny elementu <xref:System.Windows.Controls.Border> w pierwszym przykładzie. <xref:System.Windows.Controls.Border.Padding%2A> jest stosowany do elementu nadrzędnego <xref:System.Windows.Controls.Border> elementu. <xref:System.Windows.Controls.Grid> Służy do partycjonowania odstęp między trzy podrzędnych <xref:System.Windows.Controls.StackPanel> elementów. <xref:System.Windows.Controls.Button> elementy są ponownie używane, aby wyświetlić różne efekty <xref:System.Windows.FrameworkElement.Margin%2A> i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock> elementy są dodawane do każdego <xref:System.Windows.Controls.ColumnDefinition> Aby dokładniej zdefiniować różne właściwości, które są stosowane do <xref:System.Windows.Controls.Button> elementów w każdej kolumnie.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Po skompilowaniu aplikacji poprzedniego daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] który wygląda podobnie do poniższej ilustracji. Efekty różnych wartości właściwości są widoczne w odstępy między elementami i wartości właściwości istotne dla elementów w każdej kolumnie są wyświetlane w ramach <xref:System.Windows.Controls.TextBlock> elementów.  
  
 ![Kilka właściwości pozycjonowania w jednej aplikacji](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Jaka jest przyszłość  
 Właściwości zdefiniowane przez pozycjonowania <xref:System.Windows.FrameworkElement> klasy Włączanie dokładnej kontroli położenie elementu w obrębie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Masz teraz kilka technik umożliwia lepsze położenie elementów za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dodatkowe zasoby są dostępne objaśniające [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układ bardziej szczegółowo. [Przegląd panele](../../../../docs/framework/wpf/controls/panels-overview.md) temat zawiera szczegółowe informacje o różnych <xref:System.Windows.Controls.Panel> elementów. Temat [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) wprowadza zaawansowanych technik, które pozycji składników i wiązania ich działania ze źródłami danych za pomocą elementów układu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Układ](../../../../docs/framework/wpf/advanced/layout.md)
- [Przykład WPF układu galerii](https://go.microsoft.com/fwlink/?LinkID=160054)
