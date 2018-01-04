---
title: "Jak utworzyć proste lub złożone TreeViews"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a7e87295a50f901be0c7028bb2d6025b51c248c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="0a56a-102">Jak utworzyć proste lub złożone TreeViews</span><span class="sxs-lookup"><span data-stu-id="0a56a-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="0a56a-103">W tym przykładzie przedstawiono sposób tworzenia prostego lub złożonych <xref:System.Windows.Controls.TreeView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0a56a-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="0a56a-104">A <xref:System.Windows.Controls.TreeView> składa się z hierarchii <xref:System.Windows.Controls.TreeViewItem> formanty, które może zawierać ciągów tekstowych proste i również w przypadku bardziej złożonych zawartości, takich jak <xref:System.Windows.Controls.Button> formanty lub <xref:System.Windows.Controls.StackPanel> z osadzoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="0a56a-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="0a56a-105">Można jawnie definiować <xref:System.Windows.Controls.TreeView> zawartości ani źródła danych można udostępnić zawartość.</span><span class="sxs-lookup"><span data-stu-id="0a56a-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="0a56a-106">W tym temacie przedstawiono przykłady te pojęcia.</span><span class="sxs-lookup"><span data-stu-id="0a56a-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a56a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a56a-107">Example</span></span>  
 <span data-ttu-id="0a56a-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Właściwość <xref:System.Windows.Controls.TreeViewItem> z zawartością który <xref:System.Windows.Controls.TreeView> wyświetla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="0a56a-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="0a56a-109">A <xref:System.Windows.Controls.TreeViewItem> ma także <xref:System.Windows.Controls.TreeViewItem> formanty jako jego elementy podrzędne, a można zdefiniować te elementy podrzędne za pomocą <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0a56a-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="0a56a-110">Poniższy przykład przedstawia sposób jawnie definiować <xref:System.Windows.Controls.TreeViewItem> zawartości przez ustawienie <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości na ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="0a56a-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="0a56a-111">Poniższym przykładzie pokazano, jak zdefiniować elementy podrzędne <xref:System.Windows.Controls.TreeViewItem> , definiując <xref:System.Windows.Controls.ItemsControl.Items%2A> , które są <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0a56a-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="0a56a-112">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Data.XmlDataProvider> zapewnia <xref:System.Windows.Controls.TreeViewItem> zawartości i <xref:System.Windows.HierarchicalDataTemplate> definiuje wygląd elementów zawartości.</span><span class="sxs-lookup"><span data-stu-id="0a56a-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="0a56a-113">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.TreeView> gdzie <xref:System.Windows.Controls.TreeViewItem> zawartość zawiera <xref:System.Windows.Controls.DockPanel> formantów, które zostały osadzone zawartości.</span><span class="sxs-lookup"><span data-stu-id="0a56a-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0a56a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a56a-114">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="0a56a-115">TreeView — omówienie</span><span class="sxs-lookup"><span data-stu-id="0a56a-115">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="0a56a-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0a56a-116">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
