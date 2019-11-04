---
title: 'Porady: implementowanie PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459784"
---
# <a name="how-to-implement-prioritybinding"></a>Porady: implementowanie PriorityBinding
<xref:System.Windows.Data.PriorityBinding> w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] działa przez określenie listy powiązań. Lista powiązań jest uporządkowana od najwyższego priorytetu do najniższego priorytetu. Jeśli powiązanie o najwyższym priorytecie pomyślnie zwraca wartość, gdy jest przetwarzane, nigdy nie trzeba przetwarzać innych powiązań na liście. Może się tak zdarzyć, że wiązanie o najwyższym priorytecie jest czasochłonne, a następny najwyższy priorytet, który zwraca wartość, zostanie użyty do momentu, aż powiązanie o wyższym priorytecie pomyślnie zwróci wartość.  
  
## <a name="example"></a>Przykład  
 Aby zademonstrować sposób działania <xref:System.Windows.Data.PriorityBinding>, obiekt `AsyncDataSource` został utworzony z następującymi trzema właściwościami: `FastDP`, `SlowerDP`i `SlowestDP`.  
  
 Metoda dostępu get `FastDP` zwraca wartość `_fastDP` elementu członkowskiego danych.  
  
 Metoda dostępu get `SlowerDP` czeka przez 3 sekundy przed zwróceniem wartości `_slowerDP` elementu członkowskiego danych.  
  
 Metoda dostępu get `SlowestDP` czeka 5 sekund przed zwróceniem wartości `_slowestDP` elementu członkowskiego danych.  
  
> [!NOTE]
> Ten przykład służy tylko do celów demonstracyjnych. Wskazówki dotyczące platformy .NET zaleca się przed zdefiniowaniem właściwości, które są zamówieniami wielkości wolniej niż zestaw pól. Aby uzyskać więcej informacji, zobacz [Wybieranie między właściwościami i metodami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 Właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> wiąże się z powyższym `AsyncDS` za pomocą <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Gdy aparat powiązań przetwarza <xref:System.Windows.Data.Binding> obiektów, rozpoczyna się od pierwszego <xref:System.Windows.Data.Binding>, który jest powiązany z właściwością `SlowestDP`. Gdy ten <xref:System.Windows.Data.Binding> jest przetwarzany, nie zwraca wartości pomyślnie, ponieważ jest uśpiony przez 5 sekund, więc następny <xref:System.Windows.Data.Binding> element jest przetwarzany. Następny <xref:System.Windows.Data.Binding> nie zwraca wartości pomyślnie, ponieważ jest uśpiony przez 3 sekundy. Aparat powiązań następnie przechodzi do następnego elementu <xref:System.Windows.Data.Binding>, który jest powiązany z właściwością `FastDP`. Ta <xref:System.Windows.Data.Binding> zwraca wartość "Szybka wartość". W <xref:System.Windows.Controls.TextBlock> teraz zostanie wyświetlona wartość "Szybka wartość".  
  
 Po upływie 3 sekund Właściwość `SlowerDP` zwraca wartość "wolniejsza wartość". W <xref:System.Windows.Controls.TextBlock> następnie zostanie wyświetlona wartość "wolniejsza wartość".  
  
 Po upływie 5 sekund Właściwość `SlowestDP` zwraca wartość "najwolniejsza wartość". To powiązanie ma najwyższy priorytet, ponieważ jest ono wyświetlane jako pierwsze. W <xref:System.Windows.Controls.TextBlock> teraz zostanie wyświetlona wartość "najwolniejsza wartość".  
  
 Zobacz <xref:System.Windows.Data.PriorityBinding>, aby uzyskać informacje o tym, co jest uznawane za pomyślnie zwracaną wartość z powiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
