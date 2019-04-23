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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104562"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="e36c9-102">Instrukcje: Znajdowanie elementu źródłowego w obsłudze zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e36c9-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="e36c9-103">Ten przykład pokazuje, jak znaleźć element źródłowy w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e36c9-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e36c9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e36c9-104">Example</span></span>  
 <span data-ttu-id="e36c9-105">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, która jest zadeklarowana w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="e36c9-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="e36c9-106">Gdy użytkownik kliknie przycisk, dołączonego do programu obsługi, program obsługi zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="e36c9-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="e36c9-107">Kod obsługi używa <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości danych zdarzenia trasowanego, który jest zgłaszany w argumentów zdarzenia zmiany <xref:System.Windows.FrameworkElement.Width%2A> wartości właściwości w <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="e36c9-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="e36c9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e36c9-108">See also</span></span>

- <xref:System.Windows.RoutedEventArgs>
- [<span data-ttu-id="e36c9-109">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="e36c9-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="e36c9-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e36c9-110">How-to Topics</span></span>](events-how-to-topics.md)
