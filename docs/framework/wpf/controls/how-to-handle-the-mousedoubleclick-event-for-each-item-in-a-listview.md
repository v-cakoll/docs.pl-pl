---
title: 'Instrukcje: Obsługiwanie zdarzenia MouseDoubleClick dla każdego elementu w kontrolce ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962062"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="f4520-102">Instrukcje: Obsługiwanie zdarzenia MouseDoubleClick dla każdego elementu w kontrolce ListView</span><span class="sxs-lookup"><span data-stu-id="f4520-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="f4520-103">Aby obsłużyć zdarzenie dla elementu w <xref:System.Windows.Controls.ListView>, należy dodać do każdego z nich <xref:System.Windows.Controls.ListViewItem>procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f4520-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="f4520-104">Gdy jest powiązany ze źródłem danych, nie można jawnie <xref:System.Windows.Controls.ListViewItem>utworzyć, ale można obsłużyć zdarzenie dla <xref:System.Windows.EventSetter> każdego elementu, dodając do stylu <xref:System.Windows.Controls.ListViewItem>. <xref:System.Windows.Controls.ListView></span><span class="sxs-lookup"><span data-stu-id="f4520-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4520-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4520-105">Example</span></span>  
 <span data-ttu-id="f4520-106">Poniższy przykład tworzy powiązanie <xref:System.Windows.Controls.ListView> danych i <xref:System.Windows.Style> tworzy, aby dodać procedurę obsługi zdarzeń do każdego z nich <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="f4520-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="f4520-107">Poniższy przykład obsługuje <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f4520-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="f4520-108">Chociaż <xref:System.Windows.Controls.ListView> jest to najczęstsze dla powiązania ze źródłem danych, można użyć stylu, aby dodać program obsługi zdarzeń do każdego z nich <xref:System.Windows.Controls.ListViewItem> w niezwiązanym <xref:System.Windows.Controls.ListView> z danymi <xref:System.Windows.Controls.ListViewItem>bez względu na to, czy jawnie utworzysz.</span><span class="sxs-lookup"><span data-stu-id="f4520-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="f4520-109">Aby uzyskać więcej informacji na temat formantów jawnie <xref:System.Windows.Controls.ListViewItem> i niejawnie <xref:System.Windows.Controls.ItemsControl>utworzonych, zobacz.</span><span class="sxs-lookup"><span data-stu-id="f4520-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4520-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4520-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="f4520-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="f4520-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="f4520-112">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="f4520-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="f4520-113">Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath</span><span class="sxs-lookup"><span data-stu-id="f4520-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="f4520-114">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="f4520-114">ListView Overview</span></span>](listview-overview.md)
