---
title: 'Instrukcje: Znajdź element źródłowy w obsłudze zdarzeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 4cdf1434f2d341cbc1e65541fd02ab4b5cad194d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536740"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Instrukcje: Znajdź element źródłowy w obsłudze zdarzeń
Ten przykład pokazuje, jak znaleźć element źródłowy w obsłudze zdarzeń.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, która jest zadeklarowana w pliku związanym z kodem. Gdy użytkownik kliknie przycisk, dołączonego do programu obsługi, program obsługi zmiany wartości właściwości. Kod obsługi używa <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości danych zdarzenia trasowanego, który jest zgłaszany w argumentów zdarzenia zmiany <xref:System.Windows.FrameworkElement.Width%2A> wartości właściwości w <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.RoutedEventArgs>
- [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
