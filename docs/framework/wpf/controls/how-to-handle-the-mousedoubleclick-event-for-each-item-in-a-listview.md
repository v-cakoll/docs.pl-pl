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
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Instrukcje: Obsługiwanie zdarzenia MouseDoubleClick dla każdego elementu w kontrolce ListView
Aby obsłużyć zdarzenie dla elementu w <xref:System.Windows.Controls.ListView>, należy dodać do każdego z nich <xref:System.Windows.Controls.ListViewItem>procedurę obsługi zdarzeń. Gdy jest powiązany ze źródłem danych, nie można jawnie <xref:System.Windows.Controls.ListViewItem>utworzyć, ale można obsłużyć zdarzenie dla <xref:System.Windows.EventSetter> każdego elementu, dodając do stylu <xref:System.Windows.Controls.ListViewItem>. <xref:System.Windows.Controls.ListView>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy powiązanie <xref:System.Windows.Controls.ListView> danych i <xref:System.Windows.Style> tworzy, aby dodać procedurę obsługi zdarzeń do każdego z nich <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Poniższy przykład obsługuje <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzenie.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Chociaż <xref:System.Windows.Controls.ListView> jest to najczęstsze dla powiązania ze źródłem danych, można użyć stylu, aby dodać program obsługi zdarzeń do każdego z nich <xref:System.Windows.Controls.ListViewItem> w niezwiązanym <xref:System.Windows.Controls.ListView> z danymi <xref:System.Windows.Controls.ListViewItem>bez względu na to, czy jawnie utworzysz.  Aby uzyskać więcej informacji na temat formantów jawnie <xref:System.Windows.Controls.ListViewItem> i niejawnie <xref:System.Windows.Controls.ItemsControl>utworzonych, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlElement>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](listview-overview.md)
