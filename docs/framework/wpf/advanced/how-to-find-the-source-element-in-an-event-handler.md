---
title: 'Instrukcje: Znajdowanie elementu źródłowego w obsłudze zdarzeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 9a49878c9ad8313903df4506796998fd43e2e749
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104562"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Instrukcje: Znajdowanie elementu źródłowego w obsłudze zdarzeń
Ten przykład pokazuje, jak znaleźć element źródłowy w obsłudze zdarzeń.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, która jest zadeklarowana w pliku związanym z kodem. Gdy użytkownik kliknie przycisk, dołączonego do programu obsługi, program obsługi zmiany wartości właściwości. Kod obsługi używa <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości danych zdarzenia trasowanego, który jest zgłaszany w argumentów zdarzenia zmiany <xref:System.Windows.FrameworkElement.Width%2A> wartości właściwości w <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.RoutedEventArgs>
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [— Tematy porad](events-how-to-topics.md)
