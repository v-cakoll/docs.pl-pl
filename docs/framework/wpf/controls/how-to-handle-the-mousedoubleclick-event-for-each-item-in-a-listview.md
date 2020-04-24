---
title: Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646113"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView
Aby obsłużyć zdarzenie <xref:System.Windows.Controls.ListView>dla elementu w programie , <xref:System.Windows.Controls.ListViewItem>należy dodać program obsługi zdarzeń do każdego . Gdy <xref:System.Windows.Controls.ListView> a jest powiązany ze źródłem danych, <xref:System.Windows.Controls.ListViewItem>nie jawnie utworzyć , ale można <xref:System.Windows.EventSetter> obsługiwać zdarzenie <xref:System.Windows.Controls.ListViewItem>dla każdego elementu, dodając do stylu . .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dane <xref:System.Windows.Controls.ListView> powiązane <xref:System.Windows.Style> i tworzy, aby <xref:System.Windows.Controls.ListViewItem>dodać program obsługi zdarzeń do każdego .  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Poniższy przykład obsługuje <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzenie.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Chociaż najczęściej wiąże się <xref:System.Windows.Controls.ListView> ze źródłem danych, można użyć stylu, aby <xref:System.Windows.Controls.ListViewItem> dodać program obsługi zdarzeń <xref:System.Windows.Controls.ListView> do każdego w programie <xref:System.Windows.Controls.ListViewItem>innym niż dane, niezależnie od tego, czy jawnie tworzysz program .  Aby uzyskać więcej informacji na <xref:System.Windows.Controls.ListViewItem> temat jawnie i niejawnie utworzonych formantów, zobacz <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlElement>
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Powiązanie z danymi XML przy użyciu zapytań XMLDataProvider i XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](listview-overview.md)
