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
ms.openlocfilehash: a3b5805808ce2e84e7713f07694464b75d83a391
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666820"
---
# <a name="listview-overview"></a>ListView — Przegląd
<xref:System.Windows.Controls.ListView> Control oferuje infrastrukturę do wyświetlenia zbiór elementów danych w różnych układów lub widoków. Na przykład użytkownik może być do wyświetlenia elementów danych w tabeli, a także do sortowania kolumn.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>Co to jest ListView?  
 <xref:System.Windows.Controls.ListView> Formant jest <xref:System.Windows.Controls.ItemsControl> , jest tworzony na podstawie <xref:System.Windows.Controls.ListBox>. Zwykle, jego elementy są członkami kolekcji danych i są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów. A <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.Controls.ContentControl> i może zawierać tylko jeden typ elementów podrzędnych. Jednak ten element podrzędny może mieć każdy element wizualny.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Definiowanie tryb widoku dla ListView  
 Aby określić sposób wyświetlania zawartości <xref:System.Windows.Controls.ListView> kontrolki ustawisz <xref:System.Windows.Controls.ListView.View%2A> właściwości. Tryb jednego widoku, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia jest <xref:System.Windows.Controls.GridView>, który zawiera zbiór elementów danych w tabeli, która zawiera kolumny z możliwością dostosowywania.  
  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridView> dla <xref:System.Windows.Controls.ListView> formant, który wyświetla informacje dotyczące pracowników.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Poniższa ilustracja przedstawia, jak dane są wyświetlane w poprzednim przykładzie.  
  
 ![ListView z danymi wyjściowymi GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 Można utworzyć niestandardowy tryb widoku, definiując klasę, która dziedziczy po elemencie <xref:System.Windows.Controls.ViewBase> klasy. <xref:System.Windows.Controls.ViewBase> Klasy zapewnia infrastrukturę, który chcesz utworzyć widok niestandardowy. Aby uzyskać więcej informacji o tym, jak utworzyć widok niestandardowy, zobacz [Tworzenie niestandardowego trybu widoku dla ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Powiązywanie danych w ListView  
 Użyj <xref:System.Windows.Controls.ItemsControl.Items%2A> i <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości, aby określić elementy <xref:System.Windows.Controls.ListView> kontroli. Poniższy przykład ustawia <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość do zbierania danych, która jest wywoływana `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 W <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> obiektów powiązać pola określone dane. Poniższy przykład tworzy powiązanie <xref:System.Windows.Controls.GridViewColumn> obiektu do pola danych, określając <xref:System.Windows.Data.Binding> dla <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Można również określić <xref:System.Windows.Data.Binding> jako część <xref:System.Windows.DataTemplate> definicji, używanej do określania stylu komórek w kolumnie. W poniższym przykładzie <xref:System.Windows.DataTemplate> , jest identyfikowany za pomocą <xref:System.Windows.ResourceKey> ustawia <xref:System.Windows.Data.Binding> dla <xref:System.Windows.Controls.GridViewColumn>. Należy zauważyć, że w tym przykładzie nie definiuje <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> ponieważ spowoduje to więc zastępuje powiązania, który jest określony przez <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>Ustawianie stylów ListView z implementacją GridView  
 <xref:System.Windows.Controls.ListView> Kontrolka zawiera <xref:System.Windows.Controls.ListViewItem> obiektów, które reprezentują elementy danych, które są wyświetlane. Do definiowania zawartości i stylu elementów danych, można użyć następujących właściwości:  
  
-   Na <xref:System.Windows.Controls.ListView> kontrolować, należy użyć <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, i <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> właściwości.  
  
-   Na <xref:System.Windows.Controls.ListViewItem> kontrolować, należy użyć <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> właściwości.  
  
 Aby uniknąć problemów wyrównanie między komórkami w <xref:System.Windows.Controls.GridView>, nie używaj <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> do ustawiania właściwości lub dodać zawartość, która wpływa na szerokość elementu w <xref:System.Windows.Controls.ListView>. Na przykład, wyrównanie problem może wystąpić, gdy ustawisz <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Aby określić właściwości lub zdefiniować zawartość, która ma wpływ na szerokość elementów w <xref:System.Windows.Controls.GridView>, użyj właściwości <xref:System.Windows.Controls.GridView> klasy oraz ich powiązanymi klasami, takich jak <xref:System.Windows.Controls.GridViewColumn>.  
  
 Aby uzyskać więcej informacji o sposobie używania <xref:System.Windows.Controls.GridView> zobaczyć jej klasy pomocnicze [GridView — Przegląd](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 Jeśli zdefiniujesz <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla <xref:System.Windows.Controls.ListView> kontroli i również definiować <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, musi zawierać <xref:System.Windows.Controls.ContentPresenter> w stylu, aby <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> działała prawidłowo.  
  
 Nie używaj <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.ListView> zawartość, która jest wyświetlana przy użyciu <xref:System.Windows.Controls.GridView>. Aby określić wyrównanie zawartości w kolumnie <xref:System.Windows.Controls.GridView>, zdefiniuj <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Udostępnianie tego samego trybu widoku  
 Dwa <xref:System.Windows.Controls.ListView> kontrolki nie mogą udostępniać tego samego trybu widoku w tym samym czasie. Jeśli spróbujesz użyć tego samego trybu widoku z więcej niż jednym <xref:System.Windows.Controls.ListView> kontrolować, wystąpi wyjątek.  
  
 Aby określić tryb widoku, który może być jednocześnie używany przez więcej niż jedną <xref:System.Windows.Controls.ListView>, użyj szablonów i stylów. Aby uzyskać przykład sposobu definiowania widoków jako <xref:System.Windows.FrameworkElement.Resources%2A>, zobacz [ListView z wielu widoków](https://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Tworząc niestandardowy tryb widoku  
 Dostosowane widoki, takich jak <xref:System.Windows.Controls.GridView> są uzyskiwane z <xref:System.Windows.Controls.ViewBase> abstrakcyjnej klasy, która udostępnia narzędzia umożliwiające wyświetlanie elementów danych, które są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów.  
  
 Na przykład niestandardowy tryb widoku zobacz [ListView z wielu widoków](https://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Kontrolki](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
