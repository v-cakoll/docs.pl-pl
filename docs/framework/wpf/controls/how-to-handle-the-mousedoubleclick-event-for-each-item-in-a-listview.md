---
title: 'Instrukcje: Obsłuż zdarzenie MouseDoubleClick dla każdego elementu w ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: a4a93ffdf7c9cf2737c41a7fd196d8cfff716ea1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377205"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="85be8-102">Instrukcje: Obsłuż zdarzenie MouseDoubleClick dla każdego elementu w ListView</span><span class="sxs-lookup"><span data-stu-id="85be8-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="85be8-103">Aby obsłużyć zdarzenie dla elementu w <xref:System.Windows.Controls.ListView>, należy dodać program obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="85be8-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="85be8-104">Gdy <xref:System.Windows.Controls.ListView> jest powiązana ze źródłem danych, możesz nie tworzą jawnie <xref:System.Windows.Controls.ListViewItem>, ale może obsłużyć zdarzenie dla każdego elementu, dodając <xref:System.Windows.EventSetter> ze stylem <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="85be8-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85be8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="85be8-105">Example</span></span>  
 <span data-ttu-id="85be8-106">Poniższy przykład obejmuje tworzenie powiązanych z danymi <xref:System.Windows.Controls.ListView> i tworzy <xref:System.Windows.Style> dodać program obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="85be8-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="85be8-107">Następujące uchwyty przykład <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="85be8-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="85be8-108">Chociaż przeważnie można powiązać <xref:System.Windows.Controls.ListView> ze źródłem danych można użyć stylu, aby dodać program obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem> w innych — powiązane z danymi <xref:System.Windows.Controls.ListView> niezależnie od tego, czy jawnie tworzyć <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="85be8-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="85be8-109">Aby uzyskać więcej informacji na temat jawnie i niejawnie utworzony <xref:System.Windows.Controls.ListViewItem> formantów, zobacz <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="85be8-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85be8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85be8-110">See also</span></span>
- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="85be8-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="85be8-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="85be8-112">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="85be8-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="85be8-113">Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath</span><span class="sxs-lookup"><span data-stu-id="85be8-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="85be8-114">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="85be8-114">ListView Overview</span></span>](listview-overview.md)
