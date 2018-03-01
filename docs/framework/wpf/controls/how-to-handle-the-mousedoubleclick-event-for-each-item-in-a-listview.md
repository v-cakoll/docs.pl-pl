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
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Jak obsłużyć zdarzenie MouseDoubleClick dla każdego elementu w ListView
Do obsługi zdarzeń dla elementu <xref:System.Windows.Controls.ListView>, należy dodać program obsługi zdarzeń dla każdego <xref:System.Windows.Controls.ListViewItem>. Podczas <xref:System.Windows.Controls.ListView> jest powiązany ze źródłem danych nie można jawnie utworzyć <xref:System.Windows.Controls.ListViewItem>, ale może obsłużyć zdarzenia dla każdego elementu, dodając <xref:System.Windows.EventSetter> na styl z <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie tworzona z danymi <xref:System.Windows.Controls.ListView> i tworzy <xref:System.Windows.Style> można dodać obsługi zdarzeń dla każdego <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Następujący przykład uchwytów <xref:System.Windows.Controls.Control.MouseDoubleClick> zdarzeń.  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  Chociaż przeważnie powiązać <xref:System.Windows.Controls.ListView> ze źródłem danych można używać stylu można dodać obsługi zdarzeń dla każdego <xref:System.Windows.Controls.ListViewItem> w innych niż — powiązane z danymi <xref:System.Windows.Controls.ListView> niezależnie od tego, czy jawnie tworzyć <xref:System.Windows.Controls.ListViewItem>.  Aby uzyskać więcej informacji na temat jawne i niejawne utworzony <xref:System.Windows.Controls.ListViewItem> formantów, zobacz <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlElement>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)
