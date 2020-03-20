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
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145478"
---
# <a name="alignment-margins-and-padding-overview"></a>Przegląd Wyrównanie, marginesy i wypełnienia
Klasa <xref:System.Windows.FrameworkElement> udostępnia kilka właściwości, które są używane do precyzyjnego położenia elementów podrzędnych. W tym temacie omówiono cztery najważniejsze <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>właściwości: , , <xref:System.Windows.Controls.Border.Padding%2A>i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Skutki tych właściwości są ważne, aby zrozumieć, ponieważ stanowią one podstawę [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] do kontrolowania położenia elementów w aplikacjach.  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Wprowadzenie do pozycjonowania elementów  
 Istnieje wiele sposobów pozycjonować elementy za pomocą . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Jednak osiągnięcie idealnego układu wykracza <xref:System.Windows.Controls.Panel> poza zwykłe wybranie odpowiedniego elementu. Precyzyjna kontrola pozycjonowania <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>wymaga <xref:System.Windows.Controls.Border.Padding%2A>zrozumienia <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> , , i właściwości.  
  
 Na poniższej ilustracji przedstawiono scenariusz układu, który wykorzystuje kilka właściwości pozycjonowania.  
  
 ![Przykład właściwości pozycjonowania WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na pierwszy rzut <xref:System.Windows.Controls.Button> oka elementy na tej ilustracji mogą wydawać się umieszczane losowo. Jednak ich pozycje są faktycznie dokładnie kontrolowane przy użyciu kombinacji marginesów, linii trasowania i dopełnienia.  
  
 W poniższym przykładzie opisano sposób tworzenia układu na poprzedniej ilustracji. Element <xref:System.Windows.Controls.Border> hermetyzuje element <xref:System.Windows.Controls.StackPanel>nadrzędny, o <xref:System.Windows.Controls.Border.Padding%2A> wartości 15 pikseli niezależnych od urządzenia. To stanowi wąskie <xref:System.Windows.Media.Brushes.LightBlue%2A> pasmo, <xref:System.Windows.Controls.StackPanel>które otacza dziecko . Elementy podrzędne <xref:System.Windows.Controls.StackPanel> są używane do zilustrowania każdej z różnych właściwości pozycjonowania, które są szczegółowo opisane w tym temacie. Trzy <xref:System.Windows.Controls.Button> elementy są używane <xref:System.Windows.FrameworkElement.Margin%2A> do <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wykazania właściwości i właściwości.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Poniższy diagram zawiera widok z bliska różnych właściwości pozycjonowania, które są używane w poprzednim przykładzie. Kolejne sekcje w tym temacie opisują bardziej szczegółowo, jak używać każdej właściwości pozycjonowania.  
  
 ![Właściwości pozycjonowania z wyjściami&#45;połączeń ekranowych](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Opis właściwości wyrównania  
 Właściwości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> i opisują, jak element podrzędny powinien być umieszczony w przydzielonym obszarze układu elementu nadrzędnego. Korzystając z tych właściwości razem, można precyzyjnie umieścić elementy podrzędne. Na przykład elementy <xref:System.Windows.Controls.DockPanel> podrzędne a można określić <xref:System.Windows.HorizontalAlignment.Left> <xref:System.Windows.HorizontalAlignment.Right>cztery <xref:System.Windows.HorizontalAlignment.Center>różne poziome linie trasowania: , , lub , lub do <xref:System.Windows.HorizontalAlignment.Stretch> wypełnienia dostępnego miejsca. Podobne wartości są dostępne dla pozycjonowania pionowego.  
  
> [!NOTE]
> Jawnie zestaw <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> i właściwości na elemencie <xref:System.Windows.HorizontalAlignment.Stretch> mają pierwszeństwo przed wartością właściwości. Próba seta <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A>i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość `Stretch` powoduje ignorowanie `Stretch` żądania.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>Właściwość wyrównanie poziome  
 Właściwość <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> deklaruje poziome wyrównanie właściwości, aby zastosować do elementów podrzędnych. W poniższej tabeli przedstawiono <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> każdą z możliwych wartości właściwości.  
  
|Członek|Opis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Elementy podrzędne są wyrównane do lewej części przydzielonego obszaru układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Elementy podrzędne są wyrównane do środka przydzielonego obszaru układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Elementy podrzędne są wyrównane po prawej stronie przydzielonego obszaru układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>(Domyślnie)|Elementy podrzędne są rozciągnięte, aby wypełnić przydzielone miejsce w układzie elementu nadrzędnego. <xref:System.Windows.FrameworkElement.Width%2A> Jawne <xref:System.Windows.FrameworkElement.Height%2A> i wartości mają pierwszeństwo.|  
  
 W poniższym przykładzie <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> pokazano, <xref:System.Windows.Controls.Button> jak zastosować właściwość do elementów. Każda wartość atrybutu jest wyświetlana, aby lepiej zilustrować różne zachowania renderowania.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Poprzedni kod daje układ podobny do poniższej ilustracji. Efekty pozycjonowania każdej <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Próbka wyrównanie poziome](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>Właściwość verticalalignment  
 Właściwość <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> opisuje wyrównanie pionowe właściwości do zastosowania do elementów podrzędnych. W poniższej tabeli przedstawiono <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> każdą z możliwych wartości właściwości.  
  
|Członek|Opis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Elementy podrzędne są wyrównane do górnej części przydzielonego obszaru układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Center>|Elementy podrzędne są wyrównane do środka przydzielonego obszaru układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Elementy podrzędne są wyrównane do dolnej części przydzielonego obszaru układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Stretch>(Domyślnie)|Elementy podrzędne są rozciągnięte, aby wypełnić przydzielone miejsce w układzie elementu nadrzędnego. <xref:System.Windows.FrameworkElement.Width%2A> Jawne <xref:System.Windows.FrameworkElement.Height%2A> i wartości mają pierwszeństwo.|  
  
 W poniższym przykładzie <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> pokazano, <xref:System.Windows.Controls.Button> jak zastosować właściwość do elementów. Każda wartość atrybutu jest wyświetlana, aby lepiej zilustrować różne zachowania renderowania. Na potrzeby tego przykładu <xref:System.Windows.Controls.Grid> element z widocznymi liniami siatki jest używany jako element nadrzędny, aby lepiej zilustrować zachowanie układu każdej wartości właściwości.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Poprzedni kod daje układ podobny do poniższej ilustracji. Efekty pozycjonowania każdej <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Przykład właściwości VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Opis właściwości marginesu  
 Właściwość <xref:System.Windows.FrameworkElement.Margin%2A> opisuje odległość między elementem a jego elementem podrzędnym lub elementami równorzędnymi. <xref:System.Windows.FrameworkElement.Margin%2A>wartości mogą być jednolite, używając `Margin="20"`składni, takiej jak . W tej składni do <xref:System.Windows.FrameworkElement.Margin%2A> elementu zostanie zastosowana jednolita 20 pikseli niezależnych od urządzenia. <xref:System.Windows.FrameworkElement.Margin%2A>wartości mogą również przybierać formę czterech odrębnych wartości, z których każda opisuje wyraźny margines, aby `Margin="0,10,5,25"`zastosować do lewej, górnej, prawej i dolnej (w tej kolejności), na przykład . Prawidłowe użycie <xref:System.Windows.FrameworkElement.Margin%2A> właściwości umożliwia bardzo precyzyjną kontrolę pozycji renderowania elementu i pozycji renderowania jego sąsiada elementów i elementów podrzędnych.  
  
> [!NOTE]
> Margines niezerowy stosuje przestrzeń poza <xref:System.Windows.FrameworkElement.ActualWidth%2A> elementem <xref:System.Windows.FrameworkElement.ActualHeight%2A>i .  
  
 W poniższym przykładzie pokazano, jak <xref:System.Windows.Controls.Button> zastosować jednolite marginesy wokół grupy elementów. Elementy <xref:System.Windows.Controls.Button> są rozmieszczone równomiernie z buforem marginesu dziesięć pikseli w każdym kierunku.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 W wielu przypadkach jednolity margines nie jest odpowiedni. W takich przypadkach można zastosować nieujemne odstępy. W poniższym przykładzie pokazano, jak zastosować nieujemne odstępy między marginesami do elementów podrzędnych. Marginesy są opisane w tej kolejności: lewy, górny, prawy, dolny.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>
## <a name="understanding-the-padding-property"></a>Opis właściwości dopełnienie  
 Wyściółka <xref:System.Windows.FrameworkElement.Margin%2A> jest podobna do większości względów. Dopełnienie Właściwość jest narażony tylko na kilka <xref:System.Windows.Documents.Block>klas, <xref:System.Windows.Controls.Control>przede <xref:System.Windows.Controls.TextBlock> wszystkim jako wygoda: , <xref:System.Windows.Controls.Border>, i są próbki klas, które ujawniają Padding właściwości. Właściwość <xref:System.Windows.Controls.Border.Padding%2A> powiększa efektywny rozmiar elementu podrzędnego o określoną <xref:System.Windows.Thickness> wartość.  
  
 W poniższym przykładzie <xref:System.Windows.Controls.Border.Padding%2A> pokazano, <xref:System.Windows.Controls.Border> jak zastosować do elementu nadrzędnego.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Korzystanie z wyrównania, marginesów i dopełnienia w aplikacji  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> zapewnić kontrolę pozycjonowania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]niezbędną do utworzenia złożonego . Można użyć efektów każdej właściwości, aby zmienić pozycjonowanie elementu podrzędnego, umożliwiając elastyczność w tworzeniu aplikacji dynamicznych i środowiska użytkownika.  
  
 W poniższym przykładzie przedstawiono każdą z pojęć, które są szczegółowo opisane w tym temacie. Opierając się na infrastrukturze znalezionej w pierwszym przykładzie w tym temacie, w tym przykładzie dodaje <xref:System.Windows.Controls.Grid> element jako element podrzędny <xref:System.Windows.Controls.Border> w pierwszym przykładzie. <xref:System.Windows.Controls.Border.Padding%2A>jest stosowany do <xref:System.Windows.Controls.Border> elementu nadrzędnego. Jest <xref:System.Windows.Controls.Grid> używany do partycjonowania <xref:System.Windows.Controls.StackPanel> przestrzeni między trzema elementami podrzędnymi. <xref:System.Windows.Controls.Button>elementy są ponownie używane do <xref:System.Windows.FrameworkElement.Margin%2A> pokazynia różnych efektów i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock>elementy są dodawane do każdego, <xref:System.Windows.Controls.ColumnDefinition> aby lepiej <xref:System.Windows.Controls.Button> zdefiniować różne właściwości stosowane do elementów w każdej kolumnie.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Po skompilowaniu poprzednia aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] daje, który wygląda jak na poniższej ilustracji. Skutki różnych wartości właściwości są widoczne w odstępach między elementami, a istotne wartości <xref:System.Windows.Controls.TextBlock> właściwości dla elementów w każdej kolumnie są wyświetlane w elementach.  
  
 ![Kilka właściwości pozycjonowania w jednej aplikacji](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>Co dalej  
 Właściwości pozycjonowania <xref:System.Windows.FrameworkElement> zdefiniowane przez klasę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwiają precyzyjną kontrolę umieszczania elementów w aplikacjach. Masz teraz kilka technik, których można użyć, aby lepiej pozycjonować elementy za pomocą programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dostępne są dodatkowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zasoby, które wyjaśniają układ bardziej szczegółowo. Omówienie [paneli](../controls/panels-overview.md) temat zawiera <xref:System.Windows.Controls.Panel> więcej szczegółów na temat różnych elementów. Temat [Przewodnik: Moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) wprowadza zaawansowane techniki, które używają elementów układu do pozycjonowania składników i powiązania ich akcji ze źródłami danych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Przegląd Panele](../controls/panels-overview.md)
- [Układ](layout.md)
- [Przykład galerii układu WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
