---
title: 'Instrukcje: Implementowanie elementu PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: aaf2caff1e2684e08c7eb65125536f1070203d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207568"
---
# <a name="how-to-implement-prioritybinding"></a>Instrukcje: Implementowanie elementu PriorityBinding
<xref:System.Windows.Data.PriorityBinding> w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] działa, określając listę powiązania. Lista powiązania jest uporządkowana z najwyższym priorytetem do najniższego priorytetu. Jeśli powiązanie najwyższy priorytet, zwraca wartość pomyślnie, gdy jest on przetwarzany występuje nigdy nie trzeba przetworzyć pozostałych powiązaniach na liście. Może to być takim powiązanie najwyższy priorytet zajmuje dużo czasu ma zostać obliczone, dalej najwyższy priorytet, która zwraca wartość pomyślnie będzie służyć do momentu powiązanie o wyższym priorytecie zwraca wartość pomyślnie.  
  
## <a name="example"></a>Przykład  
 Aby zademonstrować sposób <xref:System.Windows.Data.PriorityBinding> działa, `AsyncDataSource` obiekt został utworzony przy użyciu następujących trzech właściwości: `FastDP`, `SlowerDP`, i `SlowestDP`.  
  
 Metody dostępu get z `FastDP` zwraca wartość `_fastDP` element członkowski danych.  
  
 Metody dostępu get z `SlowerDP` czeka na 3 sekundy przed zwróceniem wartości `_slowerDP` element członkowski danych.  
  
 Metody dostępu get z `SlowestDP` czeka na 5 sekund przed zwróceniem wartości `_slowestDP` element członkowski danych.  
  
> [!NOTE]
>  Ten przykład dotyczy tylko w celach demonstracyjnych. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Wytyczne zaleca się przed definiowania właściwości, które są rzędów wolniej, niż byłoby zestaw pól. Aby uzyskać więcej informacji, zobacz [wybór między właściwości i metody](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Właściwość wiąże się z powyższych `AsyncDS` przy użyciu <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Gdy aparat powiązania przetwarza <xref:System.Windows.Data.Binding> obiektów i zaczyna się od pierwszego <xref:System.Windows.Data.Binding>, która jest powiązana `SlowestDP` właściwości. Gdy to <xref:System.Windows.Data.Binding> jest przetwarzany, nie zwraca wartości pomyślnie ponieważ ona jest uśpiony na 5 sekund, więc następnego <xref:System.Windows.Data.Binding> jest przetwarzany element. Następne <xref:System.Windows.Data.Binding> nie zwraca wartości pomyślnie, ponieważ jest uśpiony przez 3 sekundy. Aparat powiązania następnie przechodzi do kolejnego <xref:System.Windows.Data.Binding> element, który jest powiązany z `FastDP` właściwości. To <xref:System.Windows.Data.Binding> zwraca wartość "Szybkie Value". <xref:System.Windows.Controls.TextBlock> Teraz wyświetlana jest wartość "Szybkie Value".  
  
 Po upłynie 3 sekundy `SlowerDP` właściwość zwraca wartość "Wolniejsze Value". <xref:System.Windows.Controls.TextBlock> Następnie wyświetla wartość "Wolniejsze Value".  
  
 Po upłynie 5 sekund `SlowestDP` właściwość zwraca wartość "Najwolniejsze Value". To powiązanie ma najwyższy priorytet, ponieważ ona jest wymienione jako pierwsze. <xref:System.Windows.Controls.TextBlock> Teraz wyświetlana jest wartość "Najwolniejsze Value".  
  
 Zobacz <xref:System.Windows.Data.PriorityBinding> uzyskać informacji na temat co jest uznawane za pomyślne wartość zwracana z powiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Przegląd Wiązanie danych](data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
