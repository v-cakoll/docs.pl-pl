---
title: Jak znaleźć element źródłowy w obsłudze zdarzeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: c3ae893cd7fd7780854d6eb6ffd682feadb5c5a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544007"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="e5cbe-102">Jak znaleźć element źródłowy w obsłudze zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e5cbe-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="e5cbe-103">W tym przykładzie pokazano, jak można znaleźć elementu źródłowego w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5cbe-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5cbe-104">Example</span></span>  
 <span data-ttu-id="e5cbe-105">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń, które są zadeklarowane w pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="e5cbe-106">Po kliknięciu przycisku program obsługi jest dołączony do programu obsługi zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="e5cbe-107">Kod obsługi używa <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości danych kierowanego zdarzenia, które jest zgłaszany w argumentach zdarzenia, aby zmienić <xref:System.Windows.FrameworkElement.Width%2A> wartości właściwości w <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="e5cbe-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5cbe-108">See Also</span></span>  
 <xref:System.Windows.RoutedEventArgs>  
 [<span data-ttu-id="e5cbe-109">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="e5cbe-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="e5cbe-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e5cbe-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
