---
title: 'Instrukcje: Użyj SelectedValue, SelectedValuePath i SelectedItem'
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
ms.openlocfilehash: 1bb307009586a5bbf4e9accefb633b97dc837528
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637828"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="a6dbe-102">Instrukcje: Użyj SelectedValue, SelectedValuePath i SelectedItem</span><span class="sxs-lookup"><span data-stu-id="a6dbe-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="a6dbe-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.TreeView.SelectedValue%2A> i <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości, aby określić wartość dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6dbe-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6dbe-104">Example</span></span>  
 <span data-ttu-id="a6dbe-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Właściwość zapewnia możliwość określenia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> w <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="a6dbe-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A> Reprezentuje obiekt w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji i <xref:System.Windows.Controls.TreeView> Wyświetla wartość jednej właściwości wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="a6dbe-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Właściwość określa ścieżkę do właściwości, który służy do określenia wartości <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="a6dbe-108">W przykładach w tym temacie pokazano tę koncepcję.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="a6dbe-109">W poniższym przykładzie przedstawiono <xref:System.Windows.Data.XmlDataProvider> zawierający informacje dotyczące pracowników.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="a6dbe-110">W poniższym przykładzie zdefiniowano <xref:System.Windows.HierarchicalDataTemplate> wyświetlającą `EmployeeName` i `EmployeeWorkDay` z `Employee`.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="a6dbe-111">Należy pamiętać, że <xref:System.Windows.HierarchicalDataTemplate> nie określa `EmployeeNumber` jako część szablonu.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="a6dbe-112">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.TreeView> , który używa uprzednio zdefiniowany <xref:System.Windows.HierarchicalDataTemplate> i określająca <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwość `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="a6dbe-113">Po wybraniu `EmployeeName` w <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> właściwość zwraca `EmployeeInfo` element danych, który odnosi się do wybranego `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="a6dbe-114">Jednak ponieważ <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tego <xref:System.Windows.Controls.TreeView> ustawiono `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ustawiono `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="a6dbe-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="a6dbe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6dbe-115">See also</span></span>
- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="a6dbe-116">TreeView — omówienie</span><span class="sxs-lookup"><span data-stu-id="a6dbe-116">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)
- [<span data-ttu-id="a6dbe-117">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="a6dbe-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
