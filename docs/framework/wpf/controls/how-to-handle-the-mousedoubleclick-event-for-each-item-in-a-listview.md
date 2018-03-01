---
title: "Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3fef9655ab95328e027a303df57c3359a7676eac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="ccd5b-102">Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView</span><span class="sxs-lookup"><span data-stu-id="ccd5b-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="ccd5b-103">Do obsługi zdarzeń dla elementu <xref:System.Windows.Controls.ListView>, należy dodać program obsługi zdarzeń dla każdego <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="ccd5b-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="ccd5b-104">Podczas <xref:System.Windows.Controls.ListView> jest powiązany ze źródłem danych nie można jawnie utworzyć <xref:System.Windows.Controls.ListViewItem>, ale może obsłużyć zdarzenia dla każdego elementu, dodając <xref:System.Windows.EventSetter> na styl z <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="ccd5b-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccd5b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccd5b-105">Example</span></span>  
 <span data-ttu-id="ccd5b-106">W poniższym przykładzie tworzona z danymi <xref:System.Windows.Controls.ListView> i tworzy <xref:System.Windows.Style> można dodać obsługi zdarzeń dla każdego <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="ccd5b-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="ccd5b-107">Następujący przykład uchwytów <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccd5b-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="ccd5b-108">Chociaż przeważnie powiązać <xref:System.Windows.Controls.ListView> ze źródłem danych można używać stylu można dodać obsługi zdarzeń dla każdego <xref:System.Windows.Controls.ListViewItem> w innych niż — powiązane z danymi <xref:System.Windows.Controls.ListView> niezależnie od tego, czy jawnie tworzyć <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="ccd5b-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="ccd5b-109">Aby uzyskać więcej informacji na temat jawne i niejawne utworzony <xref:System.Windows.Controls.ListViewItem> formantów, zobacz <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="ccd5b-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd5b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccd5b-110">See Also</span></span>  
 <xref:System.Xml.XmlElement>  
 [<span data-ttu-id="ccd5b-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="ccd5b-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="ccd5b-112">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="ccd5b-112">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ccd5b-113">Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath</span><span class="sxs-lookup"><span data-stu-id="ccd5b-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="ccd5b-114">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="ccd5b-114">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
