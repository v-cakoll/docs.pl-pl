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
ms.openlocfilehash: bf351b6df972dc992f214ddfe899bfa808d0cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963634"
---
# <a name="alignment-margins-and-padding-overview"></a>Przegląd Wyrównanie, marginesy i wypełnienia
<xref:System.Windows.FrameworkElement> Klasa uwidacznia kilka właściwości, które są używane do precyzyjnego pozycjonowania elementów podrzędnych. W tym temacie omówiono cztery najważniejsze właściwości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>:, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Efekty tych właściwości są ważne, ponieważ stanowią podstawę do kontrolowania położenia elementów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacjach.  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Wprowadzenie do pozycjonowania elementów  
 Istnieje wiele sposobów pozycjonowania elementów przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programu. Jednak osiągnięcie idealnych układów wykracza poza zwykłe wybranie prawego <xref:System.Windows.Controls.Panel> elementu. Precyzyjne sterowanie pozycjonowaniem <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>wymaga znajomości właściwości, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
 Na poniższej ilustracji przedstawiono scenariusz układu, który wykorzystuje kilka właściwości pozycjonowania.  
  
 ![Przykładowa Właściwość pozycjonowania WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na pierwszy rzut oka <xref:System.Windows.Controls.Button> elementy na tej ilustracji mogą wydawać się losowo umieszczane. Jednak ich położenia są w rzeczywistości precyzyjnie kontrolowane przy użyciu kombinacji marginesów, wyrównania i wypełnienia.  
  
 W poniższym przykładzie opisano sposób tworzenia układu na powyższej ilustracji. Element hermetyzuje obiekt nadrzędny <xref:System.Windows.Controls.StackPanel>o <xref:System.Windows.Controls.Border.Padding%2A> wartości 15 niezależnych pikseli urządzenia. <xref:System.Windows.Controls.Border> Te konta dla wąskiego <xref:System.Windows.Media.Brushes.LightBlue%2A> pasma otaczającego element podrzędny <xref:System.Windows.Controls.StackPanel>. Elementy podrzędne elementu <xref:System.Windows.Controls.StackPanel> są używane do ilustrowania każdej z różnych właściwości pozycjonowania, które opisano szczegółowo w tym temacie. Trzy <xref:System.Windows.Controls.Button> elementy są używane do prezentowania <xref:System.Windows.FrameworkElement.Margin%2A> właściwości i <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> .  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Poniższy diagram przedstawia widok, w którym znajdują się różne właściwości pozycjonowania, które są używane w poprzednim przykładzie. Kolejne sekcje w tym temacie opisują bardziej szczegółowo, jak używać poszczególnych właściwości pozycjonowania.  
  
 ![Pozycjonowanie właściwości z&#45;wykroczeniem ekranu](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Omówienie właściwości wyrównania  
 Właściwości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> opisują sposób umieszczania elementu podrzędnego w przydzielonym obszarze układu elementu nadrzędnego. Korzystając z tych właściwości, można precyzyjnie pozycjonować elementy podrzędne. <xref:System.Windows.Controls.DockPanel> Na przykład elementy podrzędne klasy mogą określać cztery różne Wyrównanie poziome: <xref:System.Windows.HorizontalAlignment.Right> <xref:System.Windows.HorizontalAlignment.Left>,, lub <xref:System.Windows.HorizontalAlignment.Center>, lub do <xref:System.Windows.HorizontalAlignment.Stretch> wypełnienia dostępnego miejsca. Podobne wartości są dostępne dla pozycjonowania pionowego.  
  
> [!NOTE]
> Jawnie ustawione <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości <xref:System.Windows.HorizontalAlignment.Stretch> elementu mają pierwszeństwo przed wartością właściwości. Podjęto próbę <xref:System.Windows.FrameworkElement.Height%2A>ustawienia <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> `Stretch` , i wartości wyników w `Stretch` ignorowanym żądaniu.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>Właściwość HorizontalAlignment  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Właściwość deklaruje charakterystyki wyrównania poziomego do zastosowania do elementów podrzędnych. W poniższej tabeli przedstawiono każdą z możliwych wartości <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Elementy podrzędne są wyrównane do lewej strony przydzieloną przestrzeń układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Elementy podrzędne są wyrównane do środka przydzieloną przestrzeń układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Elementy podrzędne są wyrównane do prawej strony przydzielony obszar układu elementu nadrzędnego.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>Wartooć|Elementy podrzędne są rozciągane, aby wypełnić przydzieloną przestrzeń układu elementu nadrzędnego. Wartości <xref:System.Windows.FrameworkElement.Width%2A> jawne <xref:System.Windows.FrameworkElement.Height%2A> i mają pierwszeństwo.|  
  
 Poniższy przykład pokazuje, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> jak zastosować właściwość do <xref:System.Windows.Controls.Button> elementów. Każda wartość atrybutu jest pokazywana, aby lepiej zilustrować różne zachowania renderowania.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Poprzedni kod daje układ podobny do poniższego obrazu. Efekty pozycjonowania każdej <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Przykład HorizontalAlignment](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>Właściwość VerticalAlignment  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Właściwość opisuje charakterystykę wyrównania w pionie, która ma zostać zastosowana do elementów podrzędnych. W poniższej tabeli przedstawiono każdą z możliwych wartości <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Elementy podrzędne są wyrównane do górnej krawędzi przydzieloną przestrzeń układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Center>|Elementy podrzędne są wyrównane do środka przydzieloną przestrzeń układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Elementy podrzędne są wyrównane do dolnej krawędzi przydzieloną przestrzeń układu elementu nadrzędnego.|  
|<xref:System.Windows.VerticalAlignment.Stretch>Wartooć|Elementy podrzędne są rozciągane, aby wypełnić przydzieloną przestrzeń układu elementu nadrzędnego. Wartości <xref:System.Windows.FrameworkElement.Width%2A> jawne <xref:System.Windows.FrameworkElement.Height%2A> i mają pierwszeństwo.|  
  
 Poniższy przykład pokazuje, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> jak zastosować właściwość do <xref:System.Windows.Controls.Button> elementów. Każda wartość atrybutu jest pokazywana, aby lepiej zilustrować różne zachowania renderowania. Do celów tego przykładu <xref:System.Windows.Controls.Grid> element z widocznymi liniami siatki jest używany jako obiekt nadrzędny, aby lepiej zilustrować zachowanie układu dla każdej wartości właściwości.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Poprzedni kod daje układ podobny do poniższego obrazu. Efekty pozycjonowania każdej <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> wartości są widoczne na ilustracji.  
  
 ![Przykład właściwości VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Informacje o właściwościach marginesu  
 <xref:System.Windows.FrameworkElement.Margin%2A> Właściwość opisuje odległość między elementem a jego elementami podrzędnymi lub równorzędnymi. <xref:System.Windows.FrameworkElement.Margin%2A>wartości mogą być jednorodne przy użyciu składni podobnej do `Margin="20"`. W przypadku tej składni, do <xref:System.Windows.FrameworkElement.Margin%2A> elementu zostanie zastosowana jednolita liczba pikseli niezależnych od urządzenia. <xref:System.Windows.FrameworkElement.Margin%2A>wartości mogą również przyjmować cztery różne wartości, każda wartość opisującą odrębny margines do zastosowania do lewej, górnego, prawego i dolnego (w tej kolejności), np `Margin="0,10,5,25"`. Odpowiednie użycie <xref:System.Windows.FrameworkElement.Margin%2A> właściwości umożliwia bardzo precyzyjne sterowanie pozycją renderowania elementu i pozycją renderowania elementów sąsiednich i podrzędnych.  
  
> [!NOTE]
> Margines różny od zera ma miejsce poza elementem <xref:System.Windows.FrameworkElement.ActualWidth%2A> i. <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
  
 Poniższy przykład pokazuje, jak zastosować jednolite Marginesy wokół grupy <xref:System.Windows.Controls.Button> elementów. W każdym kierunku elementy są równomiernie rozmieszczone w buforze marginesu o dziesięć pikseli. <xref:System.Windows.Controls.Button>  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 W wielu przypadkach jednolity margines nie jest odpowiedni. W takich przypadkach można zastosować niejednorodne odstępy. Poniższy przykład pokazuje, jak zastosować niejednorodne odstępy marginesu do elementów podrzędnych. Marginesy są opisane w następującej kolejności: od lewej, do góry, do prawej, do dołu.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Zrozumienie właściwości dopełnienia  
 Uzupełnienie jest podobne do <xref:System.Windows.FrameworkElement.Margin%2A> w większości. Właściwość uzupełnienie <xref:System.Windows.Documents.Block>jest uwidaczniana tylko w kilku klasach, głównie jako wygoda: <xref:System.Windows.Controls.Control>, <xref:System.Windows.Controls.Border>,, i <xref:System.Windows.Controls.TextBlock> są przykładami klas, które uwidaczniają Właściwość dopełnienia. Właściwość powiększa efektywny rozmiar elementu podrzędnego o określonej <xref:System.Windows.Thickness> wartości. <xref:System.Windows.Controls.Border.Padding%2A>  
  
 Poniższy przykład pokazuje, jak zastosować <xref:System.Windows.Controls.Border.Padding%2A> do elementu nadrzędnego. <xref:System.Windows.Controls.Border>  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Używanie wyrównania, marginesów i dopełnień w aplikacji  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]i zapewniająkontrolkępozycjonowanianiezbędnądoutworzeniazłożonej.<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Możesz użyć efektów każdej właściwości, aby zmienić położenie elementu podrzędnego, umożliwiając elastyczność w tworzeniu aplikacji dynamicznych i środowiska użytkownika.  
  
 Poniższy przykład ilustruje wszystkie koncepcje, które opisano szczegółowo w tym temacie. Kompilowanie w ramach infrastruktury, która znajduje się w pierwszym przykładzie w tym temacie, powoduje <xref:System.Windows.Controls.Grid> dodanie elementu jako elementu podrzędnego <xref:System.Windows.Controls.Border> w pierwszym przykładzie. <xref:System.Windows.Controls.Border.Padding%2A>jest zastosowany do elementu <xref:System.Windows.Controls.Border> nadrzędnego. Służy do partycjonowania przestrzeni między trzema elementami podrzędnymi <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Button>elementy są ponownie używane do wyświetlania różnych efektów <xref:System.Windows.FrameworkElement.Margin%2A> i. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.TextBlock>elementy są dodawane do każdego <xref:System.Windows.Controls.ColumnDefinition> , aby lepiej definiować różne właściwości stosowane <xref:System.Windows.Controls.Button> do elementów w każdej kolumnie.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Po skompilowaniu poprzednia aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uzyskuje podobną do poniższej ilustracji. Efekty różnych wartości właściwości są oczywiste w odstępach między elementami, a istotne wartości właściwości dla elementów w każdej kolumnie są wyświetlane w obrębie <xref:System.Windows.Controls.TextBlock> elementów.  
  
 ![Kilka właściwości pozycjonowania w jednej aplikacji](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Co dalej  
 Właściwości pozycjonowania zdefiniowane przez <xref:System.Windows.FrameworkElement> klasę umożliwiają precyzyjne sterowanie umieszczaniem elementów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjach. Teraz masz kilka technik, których można użyć do lepszego umieszczania elementów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przy użyciu programu.  
  
 Dostępne są dodatkowe zasoby, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bardziej szczegółowo objaśniają układ. Temat [Omówienie paneli](../controls/panels-overview.md) zawiera więcej szczegółów na temat różnych <xref:System.Windows.Controls.Panel> elementów. Przewodnik dotyczący tematu [: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md) klasyczna WPF wprowadza zaawansowane techniki, które używają elementów układu do pozycjonowania składników i powiązania ich działań ze źródłami danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Panele — omówienie](../controls/panels-overview.md)
- [Układ](layout.md)
- [Przykład galerii układów WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
