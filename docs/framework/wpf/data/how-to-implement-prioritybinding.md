---
title: 'Instrukcje: Implementowanie elementu PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937450"
---
# <a name="how-to-implement-prioritybinding"></a>Instrukcje: Implementowanie elementu PriorityBinding
<xref:System.Windows.Data.PriorityBinding>w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programie Works przez określenie listy powiązań. Lista powiązań jest uporządkowana od najwyższego priorytetu do najniższego priorytetu. Jeśli powiązanie o najwyższym priorytecie pomyślnie zwraca wartość, gdy jest przetwarzane, nigdy nie trzeba przetwarzać innych powiązań na liście. Może się tak zdarzyć, że wiązanie o najwyższym priorytecie jest czasochłonne, a następny najwyższy priorytet, który zwraca wartość, zostanie użyty do momentu, aż powiązanie o wyższym priorytecie pomyślnie zwróci wartość.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Data.PriorityBinding> Aby zademonstrować `AsyncDataSource` , jak działa, obiekt został utworzony z następującymi trzema właściwościami `SlowerDP`: `FastDP`, `SlowestDP`, i.  
  
 Metoda dostępu `FastDP` Get zwraca wartość `_fastDP` elementu członkowskiego danych.  
  
 Metoda dostępu `SlowerDP` Get czeka przez 3 sekundy przed zwróceniem wartości `_slowerDP` elementu członkowskiego danych.  
  
 Metoda dostępu `SlowestDP` Get czeka przez 5 sekund przed zwróceniem wartości `_slowestDP` elementu członkowskiego danych.  
  
> [!NOTE]
> Ten przykład służy tylko do celów demonstracyjnych. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Wytyczne zaleca się przed zdefiniowaniem właściwości, które są zamówieniami wielkości wolniej niż zestaw pól. Aby uzyskać więcej informacji, zobacz [Wybieranie między właściwościami i metodami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 Właściwość wiąże się z powyższym <xref:System.Windows.Data.PriorityBinding> `AsyncDS`użyciem: <xref:System.Windows.Controls.TextBlock.Text%2A>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Gdy aparat powiązań przetwarza <xref:System.Windows.Data.Binding> obiekty, zaczyna od pierwszego <xref:System.Windows.Data.Binding>, `SlowestDP` który jest powiązany z właściwością. Gdy ta <xref:System.Windows.Data.Binding> wartość jest przetwarzana, nie zwraca wartości pomyślnie, ponieważ jest uśpiony przez 5 sekund, więc następny <xref:System.Windows.Data.Binding> element jest przetwarzany. Następny <xref:System.Windows.Data.Binding> nie zwraca wartości, ponieważ jest uśpiony przez 3 sekundy. Aparat powiązań następnie przechodzi <xref:System.Windows.Data.Binding> `FastDP` do następnego elementu, który jest powiązany z właściwością. <xref:System.Windows.Data.Binding> Zwraca wartość "Szybka wartość". <xref:System.Windows.Controls.TextBlock> Teraz zostanie wyświetlona wartość "Szybka wartość".  
  
 Po upływie `SlowerDP` 3 sekund Właściwość zwraca wartość "wolniejsza wartość". <xref:System.Windows.Controls.TextBlock> Następnie zostanie wyświetlona wartość "wolniejsza wartość".  
  
 Po upływie `SlowestDP` 5 sekund Właściwość zwraca wartość "najwolniejsza wartość". To powiązanie ma najwyższy priorytet, ponieważ jest ono wyświetlane jako pierwsze. <xref:System.Windows.Controls.TextBlock> Teraz zostanie wyświetlona wartość "najwolniejsza wartość".  
  
 Zobacz <xref:System.Windows.Data.PriorityBinding> , aby uzyskać informacje o tym, co jest uznawane za pomyślnie zwracaną wartość z powiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
