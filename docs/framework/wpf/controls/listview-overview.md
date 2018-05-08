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
ms.openlocfilehash: 5a7e640b7398c2034933688ea6356ef14692f8f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="listview-overview"></a>ListView — Przegląd
<xref:System.Windows.Controls.ListView> Kontroli zapewnia infrastrukturę do wyświetlenia zbiór elementów danych w różnych układów lub widoków. Na przykład użytkownik może być do wyświetlenia elementów danych w tabeli, a także do sortowania kolumn.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>Co to jest element ListView?  
 <xref:System.Windows.Controls.ListView> Formant jest <xref:System.Windows.Controls.ItemsControl> która jest pochodną <xref:System.Windows.Controls.ListBox>. Zazwyczaj jego elementy są członkami kolekcji danych i są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów. A <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.Controls.ContentControl> i może zawierać tylko jeden podrzędny element. Ten element podrzędny można jednak każdy element wizualny.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Definiowanie tryb wyświetlania dla elementu ListView  
 Aby określić sposób wyświetlania zawartości <xref:System.Windows.Controls.ListView> kontroli, ustaw <xref:System.Windows.Controls.ListView.View%2A> właściwości. Tryb jeden widok który [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia jest <xref:System.Windows.Controls.GridView>, który zawiera kolekcję elementów danych w tabeli zawierającej kolumny można dostosowywać.  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.GridView> dla <xref:System.Windows.Controls.ListView> formant, który wyświetla informacje dotyczące pracowników.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono, jak dane są wyświetlane w poprzednim przykładzie.  
  
 ![Element ListView z danych wyjściowych w widoku GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 Można utworzyć widok niestandardowy tryb Definiowanie klasy, która dziedziczy <xref:System.Windows.Controls.ViewBase> klasy. <xref:System.Windows.Controls.ViewBase> Klasa udostępnia infrastrukturę, która należy utworzyć widok niestandardowy. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowych widoku, zobacz [utworzyć niestandardowy tryb wyświetlania na elemencie ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Wiązanie danych w elemencie ListView  
 Użyj <xref:System.Windows.Controls.ItemsControl.Items%2A> i <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości, aby określić elementy <xref:System.Windows.Controls.ListView> formantu. W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości kolekcji danych, która jest wywoływana `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 W <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> obiektów powiązać pola określone dane. Poniższy przykład wiąże <xref:System.Windows.Controls.GridViewColumn> obiektu do pola danych, określając <xref:System.Windows.Data.Binding> dla <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Można również określić <xref:System.Windows.Data.Binding> jako część <xref:System.Windows.DataTemplate> definicji, używanej do określania stylu komórki w kolumnie. W poniższym przykładzie <xref:System.Windows.DataTemplate> który jest identyfikowany przy <xref:System.Windows.ResourceKey> ustawia <xref:System.Windows.Data.Binding> dla <xref:System.Windows.Controls.GridViewColumn>. Należy pamiętać, że w tym przykładzie nie definiuje <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> , ponieważ spowoduje to zastępuje powiązania, który jest określony przez <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>Style elemencie ListView, który implementuje element GridView  
 <xref:System.Windows.Controls.ListView> Formant zawiera <xref:System.Windows.Controls.ListViewItem> obiektów, które reprezentują elementów danych, które są wyświetlane. Następujące właściwości służy do definiowania zawartości i styl elementów danych:  
  
-   Na <xref:System.Windows.Controls.ListView> kontrolować, użyj <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, i <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> właściwości.  
  
-   Na <xref:System.Windows.Controls.ListViewItem> kontrolować, użyj <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> właściwości.  
  
 Aby uniknąć problemów wyrównania między komórkami <xref:System.Windows.Controls.GridView>, nie używaj <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> do ustawiania właściwości lub dodać zawartość, która wpływa na szerokość elementu w <xref:System.Windows.Controls.ListView>. Na przykład wyrównanie problem może wystąpić, gdy ustawisz <xref:System.Windows.FrameworkElement.Margin%2A> właściwości w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Aby określić właściwości lub zdefiniuj zawartość, która wpływa na szerokość elementów w <xref:System.Windows.Controls.GridView>, użyj właściwości <xref:System.Windows.Controls.GridView> klasy i jej klas pokrewnych, takich jak <xref:System.Windows.Controls.GridViewColumn>.  
  
 Aby uzyskać więcej informacji o sposobie używania <xref:System.Windows.Controls.GridView> i jego klasy obsługi, zobacz [omówienie GridView](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 W przypadku definiowania <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla <xref:System.Windows.Controls.ListView> kontroli, a także zdefiniować <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, należy uwzględnić <xref:System.Windows.Controls.ContentPresenter> w stylu, aby <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> działała prawidłowo.  
  
 Nie używaj <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.ListView> zawartości, który jest wyświetlany za pomocą <xref:System.Windows.Controls.GridView>. Aby określić wyrównanie zawartości w kolumnie <xref:System.Windows.Controls.GridView>, zdefiniuj <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Udostępnianie tego samego trybu widoku  
 Dwa <xref:System.Windows.Controls.ListView> kontrolki nie mogą współużytkować ten sam tryb widoku w tym samym czasie. Jeśli spróbujesz użyć tego samego trybu widoku z więcej niż jednym <xref:System.Windows.Controls.ListView> kontrolować, wystąpi wyjątek.  
  
 Aby określić sposób wyświetlania, które mogą być jednocześnie używane przez więcej niż jeden <xref:System.Windows.Controls.ListView>, za pomocą szablonów lub style. Przykład sposobu definiowania widoków jako <xref:System.Windows.FrameworkElement.Resources%2A>, zobacz [element ListView z wielu widoków próbki](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Tworzenie trybu widok niestandardowy  
 Dostosowane widoków, takich jak <xref:System.Windows.Controls.GridView> pochodne <xref:System.Windows.Controls.ViewBase> abstrakcyjnej klasy, która udostępnia narzędzia do wyświetlania elementów danych, które są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów.  
  
 Na przykład widok niestandardowy tryb zobacz [element ListView z wielu widoków próbki](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Kontrolki](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
