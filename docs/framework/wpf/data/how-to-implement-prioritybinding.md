---
title: 'Porady: implementowanie PriorityBinding'
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
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e6ab8826f2298a8660a85d739fbe3456374b476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-prioritybinding"></a>Porady: implementowanie PriorityBinding
<xref:System.Windows.Data.PriorityBinding>w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] działa przez określenie listy powiązań. Lista powiązań porządkowania z najwyższym priorytetem do najniższego priorytetu. Jeśli powiązanie najwyższy priorytet zwróci wartość pomyślnie podczas przetwarzania oznacza to, że nigdy nie potrzeba przetworzyć pozostałych powiązaniach na liście. Może to być to powiązanie najwyższy priorytet trwa długo ma zostać obliczone, dalej najwyższy priorytet, która zwraca wartość pomyślnie zostanie użyty, dopóki powiązanie o wyższym priorytecie zwraca wartość pomyślnie.  
  
## <a name="example"></a>Przykład  
 Aby zademonstrować sposób <xref:System.Windows.Data.PriorityBinding> działa, `AsyncDataSource` obiekt został utworzony z następujących trzech właściwości: `FastDP`, `SlowerDP`, i `SlowestDP`.  
  
 Metody dostępu get `FastDP` zwraca wartość `_fastDP` elementu członkowskiego danych.  
  
 Metody dostępu get `SlowerDP` czeka na 3 sekundy przed zwróceniem wartość `_slowerDP` elementu członkowskiego danych.  
  
 Metody dostępu get `SlowestDP` czeka na 5 sekund przed zwróceniem wartość `_slowestDP` elementu członkowskiego danych.  
  
> [!NOTE]
>  W tym przykładzie jest tylko w celach demonstracyjnych. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Wytyczne zaleca się definiowania właściwości, które są rzędów wolniej niż zestaw pól. Aby uzyskać więcej informacji, zobacz [NIB: Wybieranie między właściwości i metody](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Właściwość jest powiązana z powyższych `AsyncDS` przy użyciu <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Gdy aparat wiązania przetwarza <xref:System.Windows.Data.Binding> obiekty, rozpoczyna się pierwszego <xref:System.Windows.Data.Binding>, która jest powiązana `SlowestDP` właściwości. Gdy to <xref:System.Windows.Data.Binding> jest przetwarzane, nie zwraca wartości pomyślnie, ponieważ jego jest uśpiony 5 sekund, więc następnej <xref:System.Windows.Data.Binding> element jest przetwarzany. Następne <xref:System.Windows.Data.Binding> nie zwraca wartości pomyślnie, ponieważ jest uśpiony przez 3 sekundy. Aparat wiązania następnie przechodzi do następnego <xref:System.Windows.Data.Binding> element, który jest powiązany z `FastDP` właściwości. To <xref:System.Windows.Data.Binding> zwraca wartość "Fast Value". <xref:System.Windows.Controls.TextBlock> Wartość "Fast wartość" są obecnie wyświetlane.  
  
 Po upłynięciu tego 3 sekundy `SlowerDP` zwraca wartość "Wolniejsze Value". <xref:System.Windows.Controls.TextBlock> Następnie wyświetla wartość "Wolniejsze wartość".  
  
 Po upłynięciu tego 5 sekund `SlowestDP` właściwość zwraca wartość "Najmniejszą wartość". Czy powiązania ma najwyższy priorytet, ponieważ znajduje się najpierw. <xref:System.Windows.Controls.TextBlock> Wartość "Najmniejszą wartość" są obecnie wyświetlane.  
  
 Zobacz <xref:System.Windows.Data.PriorityBinding> informacji o co to jest uznawany za pomyślnie wartość zwrotną z elementu powiązania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
