---
title: Jak utworzyć ListViewItems za pomocą CheckBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 424bc25f9c584017d80ba1c8f1517211595fd247
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>Jak utworzyć ListViewItems za pomocą CheckBox
W tym przykładzie przedstawiono sposób wyświetlania kolumny <xref:System.Windows.Controls.CheckBox> formantów w <xref:System.Windows.Controls.ListView> formant, który używa <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć kolumnę zawierającą <xref:System.Windows.Controls.CheckBox> formantów w <xref:System.Windows.Controls.ListView>, Utwórz <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>. Następnie ustaw <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.CheckBox>. Przykład wiąże <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> właściwość <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> wartość właściwości <xref:System.Windows.Controls.ListViewItem> go zawiera. W związku z tym, kiedy <xref:System.Windows.Controls.ListViewItem> zawierający <xref:System.Windows.Controls.CheckBox> jest zaznaczone, <xref:System.Windows.Controls.CheckBox> jest zaznaczony.  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 Poniższy przykład pokazuje, jak można utworzyć kolumny z <xref:System.Windows.Controls.CheckBox> formantów. Aby utworzyć kolumnę zestawy przykład <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> właściwość <xref:System.Windows.Controls.GridViewColumn> do <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)
