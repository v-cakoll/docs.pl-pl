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
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Instrukcje: Obsłuż zdarzenie MouseDoubleClick dla każdego elementu w ListView
Aby obsłużyć zdarzenie dla elementu w <xref:System.Windows.Controls.ListView>, należy dodać program obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem>. Gdy <xref:System.Windows.Controls.ListView> jest powiązana ze źródłem danych, możesz nie tworzą jawnie <xref:System.Windows.Controls.ListViewItem>, ale może obsłużyć zdarzenie dla każdego elementu, dodając <xref:System.Windows.EventSetter> ze stylem <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład obejmuje tworzenie powiązanych z danymi <xref:System.Windows.Controls.ListView> i tworzy <xref:System.Windows.Style> dodać program obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Następujące uchwyty przykład <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzeń.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Chociaż przeważnie można powiązać <xref:System.Windows.Controls.ListView> ze źródłem danych można użyć stylu, aby dodać program obsługi zdarzeń do każdego <xref:System.Windows.Controls.ListViewItem> w innych — powiązane z danymi <xref:System.Windows.Controls.ListView> niezależnie od tego, czy jawnie tworzyć <xref:System.Windows.Controls.ListViewItem>.  Aby uzyskać więcej informacji na temat jawnie i niejawnie utworzony <xref:System.Windows.Controls.ListViewItem> formantów, zobacz <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Xml.XmlElement>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](listview-overview.md)
