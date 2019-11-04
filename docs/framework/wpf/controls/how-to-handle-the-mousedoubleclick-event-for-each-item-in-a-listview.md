---
title: Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460232"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView
Aby obsłużyć zdarzenie dla elementu w <xref:System.Windows.Controls.ListView>, należy dodać procedurę obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem>. Gdy <xref:System.Windows.Controls.ListView> jest powiązany ze źródłem danych, nie można jawnie utworzyć <xref:System.Windows.Controls.ListViewItem>, ale można obsłużyć zdarzenie dla każdego elementu, dodając <xref:System.Windows.EventSetter> do stylu <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ListView> powiązane z danymi i tworzy <xref:System.Windows.Style>, aby dodać obsługę zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Poniższy przykład obsługuje zdarzenie <xref:System.Windows.Controls.Control.MouseDoubleClick>.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Chociaż jest to najczęstsze dla powiązania <xref:System.Windows.Controls.ListView> ze źródłem danych, można użyć stylu, aby dodać procedurę obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem> w <xref:System.Windows.Controls.ListView> niezwiązanym z danymi bez względu na to, czy jawnie utworzysz <xref:System.Windows.Controls.ListViewItem>.  Aby uzyskać więcej informacji na temat jawnie i niejawnie utworzonych kontrolek <xref:System.Windows.Controls.ListViewItem>, zobacz <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlElement>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](listview-overview.md)
