---
title: Jak użyć SelectedValue, SelectedValuePath i SelectedItem
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: 93720c0e1ac96a55fafa36479968cc3492cb0d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554797"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Jak użyć SelectedValue, SelectedValuePath i SelectedItem
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> i <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości, aby określić wartość dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Właściwość zapewnia możliwość określenia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> w <xref:System.Windows.Controls.TreeView>. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Reprezentuje obiekt w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji i <xref:System.Windows.Controls.TreeView> Wyświetla wartość jednej właściwości wybranego elementu. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Właściwość określa ścieżkę do właściwości, który służy do określenia wartości <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości. Przykłady w tym temacie przedstawiono tę koncepcję.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Data.XmlDataProvider> zawierający informacje dotyczące pracowników.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.HierarchicalDataTemplate> wyświetlający `EmployeeName` i `EmployeeWorkDay` z `Employee`. Należy pamiętać, że <xref:System.Windows.HierarchicalDataTemplate> nie określa `EmployeeNumber` w ramach szablonu.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.TreeView> używającą wcześniej zdefiniowanego <xref:System.Windows.HierarchicalDataTemplate> i który ustawia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości `EmployeeNumber`. Po wybraniu `EmployeeName` w <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> zwraca `EmployeeInfo` element danych, który odpowiada wybranej `EmployeeName`. Jednak ponieważ <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tego <xref:System.Windows.Controls.TreeView> ustawiono `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ma ustawioną wartość `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView — omówienie](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
