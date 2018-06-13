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
ms.openlocfilehash: 70eff35db638c5bfbc9c164dc381e3f58e18957b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541255"
---
# <a name="alignment-margins-and-padding-overview"></a>Przegląd Wyrównanie, marginesy i wypełnienia
<xref:System.Windows.FrameworkElement> Klasa udostępnia kilka właściwości, które są używane w celu precyzyjnego rozmieszczenia elementów podrzędnych. W tym temacie omówiono cztery z właściwości najważniejszych: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Skutki te właściwości są wziąć pod uwagę, ponieważ stanowią podstawę kontrolowanie położenie elementów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Wprowadzenie do pozycjonowania elementu  
 Istnieje wiele sposobów położenie elementów za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jednak osiągnięcia idealne układu wykracza poza po prostu Wybieranie odpowiedniej <xref:System.Windows.Controls.Panel> elementu. Pozycjonowanie precyzyjnego wymaga zrozumienia <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości.  
  
 Na poniższej ilustracji przedstawiono scenariusz układu, w którym korzysta kilka właściwości pozycjonowania.  
  
 ![Pozycjonowanie przykład właściwości WPF](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na pierwszy rzut oka <xref:System.Windows.Controls.Button> elementy na tej ilustracji może pojawić się na umieszczenie losowo. Jednak ich położenia faktycznie dokładnie są kontrolowane przez przy użyciu kombinacji marginesy, wyrównanie i dopełnienie.  
  
 Poniższy przykład zawiera opis sposobu tworzenia układu na powyższej ilustracji. A <xref:System.Windows.Controls.Border> element hermetyzuje nadrzędne <xref:System.Windows.Controls.StackPanel>, z <xref:System.Windows.Controls.Border.Padding%2A> wartość 15 pikselach niezależnych od urządzenia. To stanowi wąskie <xref:System.Windows.Media.Brushes.LightBlue%2A> pasmem wokół elementu podrzędnego <xref:System.Windows.Controls.StackPanel>. Elementy podrzędne <xref:System.Windows.Controls.StackPanel> są używane w celu zilustrowania każdego z różnych pozycjonowania właściwości, które są opisane w tym temacie. Trzy <xref:System.Windows.Controls.Button> elementy są używane do zaprezentowania zarówno <xref:System.Windows.FrameworkElement.Margin%2A> i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Na poniższym diagramie przedstawiono powiększeniu różne właściwości pozycjonowania, które są używane w poprzednim przykładzie. Kolejne sekcje w tym temacie opisano szczegółowo sposobu używania każdej właściwości pozycjonującej.  
  
 ![Właściwości pozycjonowania z ekranu wywołać&#45;dokumentów](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Opis właściwości wyrównania  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości opisują położenie elementu podrzędnego w obrębie elementu nadrzędnego układu przydzielonego miejsca. Korzystając z tych właściwości jednocześnie, można precyzyjnie pozycjonować elementy podrzędne. Na przykład elementy podrzędne <xref:System.Windows.Controls.DockPanel> można określić cztery różne wyrównanie poziome: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, lub <xref:System.Windows.HorizontalAlignment.Center>, lub do <xref:System.Windows.HorizontalAlignment.Stretch> celu wypełnienia dostępnego miejsca. Podobne wartości są dostępne na rozmieszczenie w pionie.  
  
> [!NOTE]
>  Jawnie ustaw <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości w elemencie pierwszeństwo <xref:System.Windows.HorizontalAlignment.Stretch> wartości właściwości. Trwa próba skonfigurowania <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość `Stretch` powoduje `Stretch` żądania są ignorowane.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>Właściwość HorizontalAlignment  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Właściwość deklaruje charakterystyki wyrównania poziomego do zastosowania do elementów podrzędnych. W poniższej tabeli przedstawiono listę możliwych wartości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Elementy podrzędne są wyrównane do lewej miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Elementy podrzędne są wyrównane do Centrum miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Elementy podrzędne są wyrównane z prawej strony miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Ustawienie domyślne)|Elementy podrzędne są rozciągany w celu wypełnienia miejsca przydzielonego układu elementu nadrzędnego. Jawne <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości mają pierwszeństwo.|  
  
 Poniższy przykład przedstawia sposób zastosowania <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.Controls.Button> elementów. Każda wartość atrybutu jest wyświetlany, aby lepiej zilustrować różnych zachowań renderowania.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Poprzedni kod daje podobny do poniższej ilustracji. Pozycjonowania efekty <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Właściwości HorizontalAlignment](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>Właściwość HorizontalAlignment  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Właściwość opisuje charakterystyki wyrównania poziomego do zastosowania do elementów podrzędnych. W poniższej tabeli przedstawiono możliwe wartości dla <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Elementy podrzędne są wyrównane do górnej części miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Center>|Elementy podrzędne są wyrównane do Centrum miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Elementy podrzędne są wyrównane do dolnej części miejsca przydzielonego układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Ustawienie domyślne)|Elementy podrzędne są rozciągany w celu wypełnienia miejsca przydzielonego układu elementu nadrzędnego. Jawne <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości mają pierwszeństwo.|  
  
 Poniższy przykład przedstawia sposób zastosowania <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.Controls.Button> elementów. Każda wartość atrybutu jest wyświetlany, aby lepiej zilustrować różnych zachowań renderowania. Do celów tego przykładu <xref:System.Windows.Controls.Grid> element widoczny linie siatki jest używany jako element nadrzędny, aby lepiej zilustrować zachowanie układu wartość każdej właściwości.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Poprzedni kod daje podobny do poniższej ilustracji. Pozycjonowania efekty <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Właściwości VerticalAlignment](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Opis właściwości marginesów  
 <xref:System.Windows.FrameworkElement.Margin%2A> Właściwość opisuje odległość między elementu i jego podrzędnych lub elementów równorzędnych. <xref:System.Windows.FrameworkElement.Margin%2A> Możliwe wartości jednolitego, przy użyciu składni, takich jak `Margin="20"`. Przy użyciu tej składni jednolity <xref:System.Windows.FrameworkElement.Margin%2A> 20 urządzenia pikselach niezależnych od mają zostać zastosowane do elementu. <xref:System.Windows.FrameworkElement.Margin%2A> wartości można również formę cztery różne wartości, każda wartość opisujące różne margines do zastosowania do lewej, górnej, prawej i dolnej (w tej kolejności), takich jak `Margin="0,10,5,25"`. Odpowiednie stosowanie <xref:System.Windows.FrameworkElement.Margin%2A> właściwość umożliwia bardzo precyzyjnego miejsce renderowania elementu i pozycji renderowanie elementów sąsiada i elementy podrzędne.  
  
> [!NOTE]
>  Margines niezerowy stosuje miejsca poza elementu <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Poniższy przykład przedstawia sposób zastosować uniform marginesy wokół grupy <xref:System.Windows.Controls.Button> elementów. <xref:System.Windows.Controls.Button> Elementy są równomierne buforem margines dziesięć piksel w każdym kierunku.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 W wielu przypadkach uniform margines nie jest odpowiedni. W takich przypadkach można zastosować odstępy między niejednolitego. Poniższy przykład pokazuje, jak zastosować odstępy między niejednolitego margines na elementy podrzędne. Marginesy są opisane w następującej kolejności: po lewej, top, kliknij prawym przyciskiem myszy, dołu.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Opis właściwości dopełnienia  
 Uzupełnienie jest podobny do <xref:System.Windows.FrameworkElement.Margin%2A> pod względem większości. Właściwość Padding jest narażony na tylko na kilka klas, szczególnie ze względu na wygodę: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, i <xref:System.Windows.Controls.TextBlock> są przykłady klas, które udostępniają właściwość Padding. <xref:System.Windows.Controls.Border.Padding%2A> Właściwości powiększa skuteczne rozmiar elementu podrzędnego przez określony <xref:System.Windows.Thickness> wartość.  
  
 Poniższy przykład przedstawia sposób zastosowania <xref:System.Windows.Controls.Border.Padding%2A> do elementu nadrzędnego <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Za pomocą wyrównanie marginesy i dopełnienia w aplikacji  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> udostępniają pozycjonowania kontroli niezbędnych do utworzenia złożonych [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Efekty każdej właściwości służy do zmiany elementu podrzędnego rozmieszczania, włączanie elastyczność tworzenie dynamicznych aplikacji i środowiska użytkownika.  
  
 W poniższym przykładzie pokazano każdego z założenia, które są opisane w tym temacie. Korzystając z infrastruktury znaleziono w pierwszym przykładzie w tym temacie, w tym przykładzie dodaje <xref:System.Windows.Controls.Grid> element jako element podrzędny <xref:System.Windows.Controls.Border> w pierwszym przykładzie. <xref:System.Windows.Controls.Border.Padding%2A> zastosowano do elementu nadrzędnego <xref:System.Windows.Controls.Border> elementu. <xref:System.Windows.Controls.Grid> Jest używany do partycjonowania odstęp między trzy podrzędne <xref:System.Windows.Controls.StackPanel> elementów. <xref:System.Windows.Controls.Button> elementy są ponownie używane do wyświetlenia różnych skutków <xref:System.Windows.FrameworkElement.Margin%2A> i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock> elementy są dodawane do każdego <xref:System.Windows.Controls.ColumnDefinition> Aby dokładniej zdefiniować różne właściwości stosowane do <xref:System.Windows.Controls.Button> elementów w każdej kolumnie.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Podczas kompilacji, poprzedniego aplikacji daje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czy wygląda podobnie do poniższej ilustracji. Efekty różnych wartości właściwości są widoczne w odstępy między elementami i wartości właściwości istotne dla elementów w każdej kolumnie są wyświetlane w <xref:System.Windows.Controls.TextBlock> elementów.  
  
 ![Kilka właściwości pozycjonowania w jednej aplikacji](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Co to jest dalej  
 Właściwości zdefiniowane przez pozycjonowania <xref:System.Windows.FrameworkElement> klasy włączyć precyzyjnego położenie elementu w obrębie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Masz teraz kilka technik umożliwiają lepsze położenie elementów za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dostępne są dodatkowe zasoby objaśniające [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] układu większej liczby szczegółów. [Omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md) temat zawiera szczegółowe informacje o różnych <xref:System.Windows.Controls.Panel> elementów. Temat [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) wprowadza zaawansowane techniki używające układ elementów to pozycjonowania składników i powiązać swoje działania ze źródłami danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.Margin%2A>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Układ](../../../../docs/framework/wpf/advanced/layout.md)  
 [Przykładu z galerii układu WPF](http://go.microsoft.com/fwlink/?LinkID=160054)
