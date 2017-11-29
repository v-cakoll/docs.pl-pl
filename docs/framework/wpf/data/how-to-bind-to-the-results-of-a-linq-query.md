---
title: "Jak powiązać z wynikami zapytania LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e77a0c698dae0330877c54422c15e14c82376891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Jak powiązać z wynikami zapytania LINQ
W tym przykładzie pokazano, jak do uruchomienia zapytania LINQ, a następnie powiązać z wyników.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa pola listy. Pierwsze pole listy zawiera trzy elementy listy.  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 Zaznaczenie elementu w pierwszym polu listy wywołuje następujące programu obsługi zdarzeń. W tym przykładzie `Tasks` jest kolekcją `Task` obiektów. `Task` Klasa ma właściwości o nazwie `Priority`. Zapytania LINQ, która zwraca zbiór działa ten program obsługi zdarzeń `Task` obiektów, które mają wartość priorytetu wybrany, a następnie ustawia który jako <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 Drugie pole listy jest powiązany z tej kolekcji, ponieważ jego <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ma wartość `{Binding}`. W związku z tym Wyświetla zwracanej kolekcji (na podstawie `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Zobacz też  
 [Przechowuj dane dostępne przez powiązanie w XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [Powiązania w kolekcji i wyświetlania informacji na podstawie zaznaczenia](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Nowości w wersji WPF 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
