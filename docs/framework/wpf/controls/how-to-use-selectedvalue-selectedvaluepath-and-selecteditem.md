---
title: 'Instrukcje: Używanie elementów SelectedValue, SelectedValuePath i SelectedItem'
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
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169710"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Instrukcje: Używanie elementów SelectedValue, SelectedValuePath i SelectedItem
W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.TreeView.SelectedValue%2A> i <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości, aby określić wartość dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Właściwość zapewnia możliwość określenia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> w <xref:System.Windows.Controls.TreeView>. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Reprezentuje obiekt w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji i <xref:System.Windows.Controls.TreeView> Wyświetla wartość jednej właściwości wybranego elementu. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Właściwość określa ścieżkę do właściwości, który służy do określenia wartości <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości. W przykładach w tym temacie pokazano tę koncepcję.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Data.XmlDataProvider> zawierający informacje dotyczące pracowników.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.HierarchicalDataTemplate> wyświetlającą `EmployeeName` i `EmployeeWorkDay` z `Employee`. Należy pamiętać, że <xref:System.Windows.HierarchicalDataTemplate> nie określa `EmployeeNumber` jako część szablonu.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.TreeView> , który używa uprzednio zdefiniowany <xref:System.Windows.HierarchicalDataTemplate> i określająca <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwość `EmployeeNumber`. Po wybraniu `EmployeeName` w <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> właściwość zwraca `EmployeeInfo` element danych, który odnosi się do wybranego `EmployeeName`. Jednak ponieważ <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tego <xref:System.Windows.Controls.TreeView> ustawiono `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ustawiono `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView — Przegląd](treeview-overview.md)
- [— Tematy porad](treeview-how-to-topics.md)
