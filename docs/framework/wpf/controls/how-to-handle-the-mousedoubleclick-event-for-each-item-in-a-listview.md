---
title: 'Instrukcje: Obsługiwanie zdarzenia MouseDoubleClick dla każdego elementu w kontrolce ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 443e5c620ef5bf240d3e317f0234aac0b29b456f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145083"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Instrukcje: Obsługiwanie zdarzenia MouseDoubleClick dla każdego elementu w kontrolce ListView
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
- [Przegląd Wiązanie danych](../data/data-binding-overview.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Wiązanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — Przegląd](listview-overview.md)
