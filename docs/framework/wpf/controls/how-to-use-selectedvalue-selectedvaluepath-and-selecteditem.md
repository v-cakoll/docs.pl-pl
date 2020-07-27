---
title: Jak użyć SelectedValue, SelectedValuePath i SelectedItem
description: Dowiedz się, jak użyć właściwości SelectedValue i SelectedValuePath, aby określić wartość dla SelectedItem Windows Presentation Foundation TreeView.
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
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166279"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="fd0a8-103">Jak użyć SelectedValue, SelectedValuePath i SelectedItem</span><span class="sxs-lookup"><span data-stu-id="fd0a8-103">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="fd0a8-104">Ten przykład pokazuje, jak użyć <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości i, <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Aby określić wartość dla <xref:System.Windows.Controls.TreeView.SelectedItem%2A> a <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-104">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd0a8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd0a8-105">Example</span></span>  
 <span data-ttu-id="fd0a8-106"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Właściwość umożliwia określenie <xref:System.Windows.Controls.TreeView.SelectedValue%2A> dla elementu <xref:System.Windows.Controls.TreeView.SelectedItem%2A> w <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-106">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="fd0a8-107"><xref:System.Windows.Controls.TreeView.SelectedItem%2A>Reprezentuje obiekt w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji i <xref:System.Windows.Controls.TreeView> wyświetla wartość pojedynczej właściwości wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-107">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="fd0a8-108"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Właściwość określa ścieżkę do właściwości, która jest używana do określenia wartości <xref:System.Windows.Controls.TreeView.SelectedValue%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-108">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="fd0a8-109">Przykłady w tym temacie ilustrują tę koncepcję.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-109">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="fd0a8-110">Poniższy przykład pokazuje <xref:System.Windows.Data.XmlDataProvider> , który zawiera informacje o pracowniku.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-110">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="fd0a8-111">W poniższym przykładzie zdefiniowano <xref:System.Windows.HierarchicalDataTemplate> , który wyświetla `EmployeeName` i `EmployeeWorkDay` `Employee` .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-111">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="fd0a8-112">Należy zauważyć, że program nie <xref:System.Windows.HierarchicalDataTemplate> określa `EmployeeNumber` jako części szablonu.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-112">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="fd0a8-113">Poniższy przykład pokazuje <xref:System.Windows.Controls.TreeView> , że używa poprzednio zdefiniowanego <xref:System.Windows.HierarchicalDataTemplate> i ustawia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> Właściwość na `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-113">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="fd0a8-114">Po wybraniu `EmployeeName` w <xref:System.Windows.Controls.TreeView> , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość zwraca `EmployeeInfo` element danych, który odpowiada wybranemu `EmployeeName` .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-114">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="fd0a8-115">Jednak ponieważ dla <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tego ustawienia ustawiono wartość <xref:System.Windows.Controls.TreeView> `EmployeeNumber` , <xref:System.Windows.Controls.TreeView.SelectedValue%2A> jest ustawiona na `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-115">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="fd0a8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd0a8-116">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="fd0a8-117">TreeView — Przegląd</span><span class="sxs-lookup"><span data-stu-id="fd0a8-117">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="fd0a8-118">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="fd0a8-118">How-to Topics</span></span>](treeview-how-to-topics.md)
