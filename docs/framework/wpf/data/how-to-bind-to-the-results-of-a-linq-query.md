---
title: Jak powiązać z wynikami zapytania LINQ
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d374bb69b6b7e022497403b9591b27e9ad7e2395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554996"
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
 [Udostępnianie danych do powiązania w XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Nowości w WPF w wersji 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
