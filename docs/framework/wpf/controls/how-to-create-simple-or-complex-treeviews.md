---
title: 'Instrukcje: Utwórz proste lub złożone TreeViews'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: d6f9653304b67948d8a8995d1582cb10b012ee06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609138"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="36e59-102">Instrukcje: Utwórz proste lub złożone TreeViews</span><span class="sxs-lookup"><span data-stu-id="36e59-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="36e59-103">W tym przykładzie pokazano, jak utworzyć proste lub złożone <xref:System.Windows.Controls.TreeView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="36e59-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="36e59-104">A <xref:System.Windows.Controls.TreeView> składa się z hierarchią <xref:System.Windows.Controls.TreeViewItem> formanty, które mogą zawierać ciągi zwykły tekst i również bardziej złożonych zawartości, takie jak <xref:System.Windows.Controls.Button> kontrolki lub <xref:System.Windows.Controls.StackPanel> przy użyciu osadzonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="36e59-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="36e59-105">Można jawnie określić <xref:System.Windows.Controls.TreeView> zawartości lub źródło danych może zapewnić zawartości.</span><span class="sxs-lookup"><span data-stu-id="36e59-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="36e59-106">Ten temat zawiera przykłady tych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="36e59-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36e59-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="36e59-107">Example</span></span>  
 <span data-ttu-id="36e59-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Właściwość <xref:System.Windows.Controls.TreeViewItem> z zawartością, <xref:System.Windows.Controls.TreeView> wyświetla dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="36e59-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="36e59-109">A <xref:System.Windows.Controls.TreeViewItem> może także zawierać <xref:System.Windows.Controls.TreeViewItem> służy jako jego elementy podrzędne i można zdefiniować te elementy podrzędne przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="36e59-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="36e59-110">Poniższy przykład pokazuje, jak jawne zdefiniowanie <xref:System.Windows.Controls.TreeViewItem> zawartości, ustawiając <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwość ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="36e59-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="36e59-111">Poniższy przykład pokazują, jak zdefiniować elementy podrzędne <xref:System.Windows.Controls.TreeViewItem> , definiując <xref:System.Windows.Controls.ItemsControl.Items%2A> , które są <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="36e59-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="36e59-112">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Data.XmlDataProvider> zapewnia <xref:System.Windows.Controls.TreeViewItem> zawartości i <xref:System.Windows.HierarchicalDataTemplate> definiuje wygląd elementów zawartości.</span><span class="sxs-lookup"><span data-stu-id="36e59-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="36e59-113">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Controls.TreeViewItem> zawartość zawiera <xref:System.Windows.Controls.DockPanel> formantów, które zostały osadzone zawartości.</span><span class="sxs-lookup"><span data-stu-id="36e59-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="36e59-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36e59-114">See also</span></span>
- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="36e59-115">TreeView — omówienie</span><span class="sxs-lookup"><span data-stu-id="36e59-115">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)
- [<span data-ttu-id="36e59-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="36e59-116">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
