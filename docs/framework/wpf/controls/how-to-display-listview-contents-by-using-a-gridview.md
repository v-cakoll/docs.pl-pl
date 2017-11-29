---
title: "Jak wyświetlić zawartość ListView przy użyciu GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24560a1e9b663a3145b589b5a03af8a8b72236ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="6f4a4-102">Jak wyświetlić zawartość ListView przy użyciu GridView</span><span class="sxs-lookup"><span data-stu-id="6f4a4-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="6f4a4-103">W tym przykładzie pokazano sposób definiowania <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="6f4a4-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f4a4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f4a4-104">Example</span></span>  
 <span data-ttu-id="6f4a4-105">Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6f4a4-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="6f4a4-106">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.GridViewColumn> obiektów, które powiązania do określonego dla zawartości danych <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="6f4a4-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="6f4a4-107">To <xref:System.Windows.Controls.GridView> przykładzie trzy <xref:System.Windows.Controls.GridViewColumn> obiektów, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest ustawiony jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="6f4a4-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="6f4a4-108">Na poniższej ilustracji przedstawiono sposób wyświetlania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6f4a4-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="6f4a4-109">![Element ListView z danych wyjściowych w widoku GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="6f4a4-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4a4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f4a4-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="6f4a4-111">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="6f4a4-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="6f4a4-112">Omówienie widoku GridView</span><span class="sxs-lookup"><span data-stu-id="6f4a4-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="6f4a4-113">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="6f4a4-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
