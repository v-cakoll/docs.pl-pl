---
title: ListView — Przegląd
description: Dowiedz się więcej o Windows Presentation Foundation formancie ListView, który zapewnia infrastrukturę do wyświetlania elementów danych w różnych układach lub widokach.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164566"
---
# <a name="listview-overview"></a>ListView — Przegląd
<xref:System.Windows.Controls.ListView>Kontrolka udostępnia infrastrukturę do wyświetlania zestawu elementów danych w różnych układach lub widokach. Na przykład użytkownik może chcieć wyświetlić elementy danych w tabeli, a także sortować jego kolumny.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>Co to jest widok ListView?  
 <xref:System.Windows.Controls.ListView>Kontrolka jest <xref:System.Windows.Controls.ItemsControl> pochodną <xref:System.Windows.Controls.ListBox> . Zazwyczaj jego elementy są elementami członkowskimi kolekcji danych i są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiekty. A <xref:System.Windows.Controls.ListViewItem> <xref:System.Windows.Controls.ContentControl> i może zawierać tylko jeden element podrzędny. Jednak ten element podrzędny może być dowolnym elementem wizualizacji.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Definiowanie trybu widoku dla elementu ListView  
 Aby określić tryb wyświetlania zawartości <xref:System.Windows.Controls.ListView> kontrolki, należy ustawić <xref:System.Windows.Controls.ListView.View%2A> Właściwość. Jest to jeden tryb widoku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , który zapewnia <xref:System.Windows.Controls.GridView> , który wyświetla kolekcję elementów danych w tabeli, która ma dostosowywalne kolumny.  
  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.GridView> dla <xref:System.Windows.Controls.ListView> kontrolki, która wyświetla informacje o pracownikach.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono, jak dane są wyświetlane w poprzednim przykładzie.  
  
 ![Zrzut ekranu pokazujący widok ListView z danymi wyjściowymi GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Niestandardowy tryb widoku można utworzyć, definiując klasę, która dziedziczy z <xref:System.Windows.Controls.ViewBase> klasy. <xref:System.Windows.Controls.ViewBase>Klasa udostępnia infrastrukturę, która jest potrzebna do utworzenia widoku niestandardowego. Aby uzyskać więcej informacji na temat tworzenia widoku niestandardowego, zobacz [Tworzenie niestandardowego trybu widoku dla elementu ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Powiązywanie danych z elementem ListView  
 Użyj <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości i, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Aby określić elementy dla <xref:System.Windows.Controls.ListView> kontrolki. Poniższy przykład ustawia <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość na kolekcję danych, która jest wywoływana `EmployeeInfoDataSource` .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 W <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumn> obiekcie obiekty są powiązane z określonymi polami danych. Poniższy przykład wiąże <xref:System.Windows.Controls.GridViewColumn> obiekt z polem danych przez określenie <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Można również określić <xref:System.Windows.Data.Binding> jako część <xref:System.Windows.DataTemplate> definicji, która będzie używana do stylu komórek w kolumnie. W poniższym przykładzie, <xref:System.Windows.DataTemplate> który jest identyfikowany z <xref:System.Windows.ResourceKey> zestawem <xref:System.Windows.Data.Binding> dla <xref:System.Windows.Controls.GridViewColumn> . Należy zauważyć, że w tym przykładzie nie jest zdefiniowane, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> ponieważ spowodowałoby to zastąpienie powiązania, które jest określone przez <xref:System.Windows.DataTemplate> .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Określanie stylu elementu ListView, który implementuje GridView  
 <xref:System.Windows.Controls.ListView>Formant zawiera <xref:System.Windows.Controls.ListViewItem> obiekty, które reprezentują elementy danych, które są wyświetlane. Można użyć następujących właściwości do zdefiniowania zawartości i stylu elementów danych:  
  
- Na <xref:System.Windows.Controls.ListView> kontrolce Użyj <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> właściwości, i <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> .  
  
- Na <xref:System.Windows.Controls.ListViewItem> kontrolce Użyj <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> właściwości i.  
  
 Aby uniknąć problemów z wyrównaniami między komórkami w, nie należy <xref:System.Windows.Controls.GridView> używać <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> do ustawiania właściwości ani dodawania zawartości, która wpływa na szerokość elementu w <xref:System.Windows.Controls.ListView> . Na przykład problem wyrównany może wystąpić po ustawieniu <xref:System.Windows.FrameworkElement.Margin%2A> właściwości w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> . Aby określić właściwości lub zdefiniować zawartość wpływającą na szerokość elementów w <xref:System.Windows.Controls.GridView> , użyj właściwości <xref:System.Windows.Controls.GridView> klasy i jej klas pokrewnych, takich jak <xref:System.Windows.Controls.GridViewColumn> .  
  
 Aby uzyskać więcej informacji o sposobach korzystania z <xref:System.Windows.Controls.GridView> i jej klasy pomocniczej, zobacz widok [GridView](gridview-overview.md).  
  
 Jeśli zdefiniujesz <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla <xref:System.Windows.Controls.ListView> kontrolki, a także zdefiniujesz <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> , musisz uwzględnić <xref:System.Windows.Controls.ContentPresenter> w stylu, aby <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> działał poprawnie.  
  
 Nie należy używać <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> dla <xref:System.Windows.Controls.ListView> zawartości, która jest wyświetlana przy użyciu <xref:System.Windows.Controls.GridView> . Aby określić wyrównanie zawartości w kolumnie a <xref:System.Windows.Controls.GridView> , zdefiniuj <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Udostępnianie tego samego trybu widoku  
 Dwie <xref:System.Windows.Controls.ListView> kontrolki nie mogą współużytkować tego samego trybu widoku jednocześnie. Jeśli spróbujesz użyć tego samego trybu widoku z więcej niż jedną <xref:System.Windows.Controls.ListView> kontrolką, wystąpi wyjątek.  
  
 Aby określić tryb widoku, który może być jednocześnie używany przez więcej niż jeden <xref:System.Windows.Controls.ListView> , użyj szablonów lub stylów.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Tworzenie niestandardowego trybu widoku  
 Niestandardowe widoki, takie jak pochodzą <xref:System.Windows.Controls.GridView> z <xref:System.Windows.Controls.ViewBase> klasy abstrakcyjnej, które udostępniają narzędzia do wyświetlania elementów danych, które są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiekty.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView — Przegląd](gridview-overview.md)
- [— Tematy porad](listview-how-to-topics.md)
- [Formanty](../advanced/optimizing-performance-controls.md)
