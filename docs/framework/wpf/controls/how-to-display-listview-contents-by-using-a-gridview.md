---
title: Jak wyświetlić zawartość ListView przy użyciu GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554054"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="8d977-102">Jak wyświetlić zawartość ListView przy użyciu GridView</span><span class="sxs-lookup"><span data-stu-id="8d977-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="8d977-103">W tym przykładzie pokazano sposób definiowania <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="8d977-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d977-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d977-104">Example</span></span>  
 <span data-ttu-id="8d977-105">Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów.</span><span class="sxs-lookup"><span data-stu-id="8d977-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="8d977-106">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.GridViewColumn> obiektów, które powiązania do określonego dla zawartości danych <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="8d977-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="8d977-107">To <xref:System.Windows.Controls.GridView> przykładzie trzy <xref:System.Windows.Controls.GridViewColumn> obiektów, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest ustawiony jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="8d977-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="8d977-108">Na poniższej ilustracji przedstawiono sposób wyświetlania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8d977-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="8d977-109">![Element ListView z danych wyjściowych w widoku GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="8d977-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d977-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d977-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="8d977-111">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="8d977-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="8d977-112">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="8d977-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="8d977-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8d977-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
