---
title: ListView — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187522"
---
# <a name="listview-overview"></a>ListView — Przegląd
Formant <xref:System.Windows.Controls.ListView> zapewnia infrastrukturę do wyświetlania zestawu elementów danych w różnych układach lub widokach. Na przykład użytkownik może chcieć wyświetlić elementy danych w tabeli, a także posortować jego kolumny.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>Co to jest ListView?  
 Formant <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl> jest, który pochodzi <xref:System.Windows.Controls.ListBox>od . Zazwyczaj jego elementy są członkami kolekcji danych i <xref:System.Windows.Controls.ListViewItem> są reprezentowane jako obiekty. A <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.Controls.ContentControl> i może zawierać tylko jeden element podrzędny. Jednak ten element podrzędny może być dowolny element wizualny.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Definiowanie trybu widoku dla widoku listview  
 Aby określić tryb widoku dla <xref:System.Windows.Controls.ListView> zawartości formantu, należy ustawić <xref:System.Windows.Controls.ListView.View%2A> właściwość. Jeden tryb [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] widoku, <xref:System.Windows.Controls.GridView>który zapewnia jest , który wyświetla zbiór elementów danych w tabeli, która ma konfigurowalne kolumny.  
  
 W poniższym <xref:System.Windows.Controls.GridView> przykładzie pokazano, <xref:System.Windows.Controls.ListView> jak zdefiniować formantu, który wyświetla informacje o pracownikach.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji pokazano, jak dane są wyświetlane w poprzednim przykładzie.  
  
 ![Zrzut ekranu przedstawiający widok list z wyjściem GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Można utworzyć tryb widoku niestandardowego, definiując klasę, która dziedziczy z <xref:System.Windows.Controls.ViewBase> klasy. Klasa <xref:System.Windows.Controls.ViewBase> zapewnia infrastrukturę, która jest potrzebna do utworzenia widoku niestandardowego. Aby uzyskać więcej informacji na temat tworzenia widoku niestandardowego, zobacz [Tworzenie trybu widoku niestandardowego dla widoku listview](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Powiązanie danych z listview  
 Użyj <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i, aby określić elementy dla <xref:System.Windows.Controls.ListView> formantu. Poniższy przykład <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ustawia właściwość do kolekcji danych, która jest wywoływana `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 W <xref:System.Windows.Controls.GridView>polu <xref:System.Windows.Controls.GridViewColumn> , obiekty wiążą się z określonymi polami danych. Poniższy przykład wiąże <xref:System.Windows.Controls.GridViewColumn> obiekt z polem danych, określając <xref:System.Windows.Data.Binding> dla <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Można również określić <xref:System.Windows.Data.Binding> jako <xref:System.Windows.DataTemplate> część definicji używanej do stylowania komórek w kolumnie. <xref:System.Windows.DataTemplate> W poniższym przykładzie, który jest <xref:System.Windows.ResourceKey> identyfikowany z zestawami <xref:System.Windows.Data.Binding> for a <xref:System.Windows.Controls.GridViewColumn>. Należy zauważyć, że w <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> tym przykładzie nie definiuje, ponieważ <xref:System.Windows.DataTemplate>w ten sposób zastępuje powiązanie, które jest określone przez .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Stylowanie widoku list, który implementuje GridView  
 Formant <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ListViewItem> zawiera obiekty, które reprezentują elementy danych, które są wyświetlane. Do zdefiniowania zawartości i stylu elementów danych można użyć następujących właściwości:  
  
- W <xref:System.Windows.Controls.ListView> formancie <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>użyj <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> i właściwości.  
  
- Na <xref:System.Windows.Controls.ListViewItem> formancie <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> użyj <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> właściwości i.  
  
 Aby uniknąć problemów z <xref:System.Windows.Controls.GridView>wyrównaniem między <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> komórkami w , nie należy używać do ustawiania <xref:System.Windows.Controls.ListView>właściwości lub dodawania zawartości, która wpływa na szerokość elementu w pliku . Na przykład problem wyrównania może wystąpić <xref:System.Windows.FrameworkElement.Margin%2A> po <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>ustawieniu właściwości w pliku . Aby określić właściwości lub zdefiniować zawartość, która <xref:System.Windows.Controls.GridView>wpływa na szerokość <xref:System.Windows.Controls.GridView> elementów w , użyj <xref:System.Windows.Controls.GridViewColumn>właściwości klasy i jej powiązanych klas, takich jak .  
  
 Aby uzyskać więcej informacji <xref:System.Windows.Controls.GridView> na temat używania i jego klas pomocniczych, zobacz [Omówienie widoku GridView](gridview-overview.md).  
  
 Jeśli definiujesz <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> formantu, a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>także definiujesz <xref:System.Windows.Controls.ContentPresenter> , należy dołączyć <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> w stylu, aby działał poprawnie.  
  
 Nie należy <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> używać <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.ListView> i dla zawartości, która <xref:System.Windows.Controls.GridView>jest wyświetlana za pomocą pliku . Aby określić wyrównanie zawartości w <xref:System.Windows.Controls.GridView>kolumnie <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, zdefiniuj plik .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Udostępnianie tego samego trybu widoku  
 Dwa <xref:System.Windows.Controls.ListView> formanty nie mogą współużytkuje tego samego trybu widoku w tym samym czasie. Jeśli spróbujesz użyć tego samego trybu <xref:System.Windows.Controls.ListView> widoku z więcej niż jednym formantem, wystąpi wyjątek.  
  
 Aby określić tryb widoku, który może być <xref:System.Windows.Controls.ListView>jednocześnie używany przez więcej niż jeden , użyj szablonów lub stylów.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Tworzenie trybu widoku niestandardowego  
 Widoki dostosowane, <xref:System.Windows.Controls.GridView> takie jak <xref:System.Windows.Controls.ViewBase> pochodzą z klasy abstrakcyjnej, która udostępnia narzędzia <xref:System.Windows.Controls.ListViewItem> do wyświetlania elementów danych, które są reprezentowane jako obiekty.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView — omówienie](gridview-overview.md)
- [Tematy in jakże](listview-how-to-topics.md)
- [Kontrolki](../advanced/optimizing-performance-controls.md)
