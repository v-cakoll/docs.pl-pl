---
title: 'Instrukcje: Tworzenie prostej lub złożonej kontrolki TreeView'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 7edb4933ebcc0f0d2cb02754238c2342ee9dd4a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205150"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="df0dc-102">Instrukcje: Tworzenie prostej lub złożonej kontrolki TreeView</span><span class="sxs-lookup"><span data-stu-id="df0dc-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="df0dc-103">W tym przykładzie pokazano, jak utworzyć proste lub złożone <xref:System.Windows.Controls.TreeView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="df0dc-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="df0dc-104">A <xref:System.Windows.Controls.TreeView> składa się z hierarchią <xref:System.Windows.Controls.TreeViewItem> formanty, które mogą zawierać ciągi zwykły tekst i również bardziej złożonych zawartości, takie jak <xref:System.Windows.Controls.Button> kontrolki lub <xref:System.Windows.Controls.StackPanel> przy użyciu osadzonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="df0dc-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="df0dc-105">Można jawnie określić <xref:System.Windows.Controls.TreeView> zawartości lub źródło danych może zapewnić zawartości.</span><span class="sxs-lookup"><span data-stu-id="df0dc-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="df0dc-106">Ten temat zawiera przykłady tych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="df0dc-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df0dc-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="df0dc-107">Example</span></span>  
 <span data-ttu-id="df0dc-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Właściwość <xref:System.Windows.Controls.TreeViewItem> z zawartością, <xref:System.Windows.Controls.TreeView> wyświetla dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="df0dc-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="df0dc-109">A <xref:System.Windows.Controls.TreeViewItem> może także zawierać <xref:System.Windows.Controls.TreeViewItem> służy jako jego elementy podrzędne i można zdefiniować te elementy podrzędne przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="df0dc-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="df0dc-110">Poniższy przykład pokazuje, jak jawne zdefiniowanie <xref:System.Windows.Controls.TreeViewItem> zawartości, ustawiając <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwość ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="df0dc-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="df0dc-111">Poniższy przykład pokazują, jak zdefiniować elementy podrzędne <xref:System.Windows.Controls.TreeViewItem> , definiując <xref:System.Windows.Controls.ItemsControl.Items%2A> , które są <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="df0dc-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="df0dc-112">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Data.XmlDataProvider> zapewnia <xref:System.Windows.Controls.TreeViewItem> zawartości i <xref:System.Windows.HierarchicalDataTemplate> definiuje wygląd elementów zawartości.</span><span class="sxs-lookup"><span data-stu-id="df0dc-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="df0dc-113">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Controls.TreeViewItem> zawartość zawiera <xref:System.Windows.Controls.DockPanel> formantów, które zostały osadzone zawartości.</span><span class="sxs-lookup"><span data-stu-id="df0dc-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="df0dc-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df0dc-114">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="df0dc-115">TreeView — omówienie</span><span class="sxs-lookup"><span data-stu-id="df0dc-115">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="df0dc-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="df0dc-116">How-to Topics</span></span>](treeview-how-to-topics.md)
