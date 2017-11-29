---
title: "Jak znaleźć element źródłowy w obsłudze zdarzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9746683ec5b7ad142591c2b419f9af21be8d69c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Jak znaleźć element źródłowy w obsłudze zdarzeń
W tym przykładzie pokazano, jak można znaleźć elementu źródłowego w obsłudze zdarzeń.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń, które są zadeklarowane w pliku CodeBehind. Po kliknięciu przycisku program obsługi jest dołączony do programu obsługi zmiany wartości właściwości. Kod obsługi używa <xref:System.Windows.RoutedEventArgs.Source%2A> właściwości danych kierowanego zdarzenia, które jest zgłaszany w argumentach zdarzenia, aby zmienić <xref:System.Windows.FrameworkElement.Width%2A> wartości właściwości w <xref:System.Windows.RoutedEventArgs.Source%2A> elementu.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.RoutedEventArgs>  
 [Omówienie kierowane zdarzenia](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
