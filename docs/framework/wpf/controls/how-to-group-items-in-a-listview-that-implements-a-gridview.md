---
title: Jak grupować elementy w ListView, który implementuje GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551911"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="ecbaf-102">Jak grupować elementy w ListView, który implementuje GridView</span><span class="sxs-lookup"><span data-stu-id="ecbaf-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="ecbaf-103">W tym przykładzie przedstawiono sposób wyświetlania grup elementów w <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecbaf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecbaf-104">Example</span></span>  
 <span data-ttu-id="ecbaf-105">Aby wyświetlić grupy elementów w <xref:System.Windows.Controls.ListView>, zdefiniuj <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="ecbaf-106">W poniższym przykładzie przedstawiono <xref:System.Windows.Data.CollectionViewSource> który grupuje elementy danych zgodnie z wartością `Catalog` pola danych.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="ecbaf-107">W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.ListView> do <xref:System.Windows.Data.CollectionViewSource> definiujący w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="ecbaf-108">Definiuje również przykładzie <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> implementującej <xref:System.Windows.Controls.Expander> formantu.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="ecbaf-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecbaf-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="ecbaf-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ecbaf-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="ecbaf-111">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="ecbaf-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="ecbaf-112">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="ecbaf-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
