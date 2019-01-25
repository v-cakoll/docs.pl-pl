---
title: 'Instrukcje: Powiąż z wynikami zapytania LINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: f39715cbfa0fe861f369ab313ac8fad11a347dbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583071"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Instrukcje: Powiąż z wynikami zapytania LINQ
W tym przykładzie pokazano, jak uruchomić zapytanie LINQ, a następnie wiążą się z wynikami.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa pola listy. Na pierwszej liście zawiera trzy elementy listy.  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 Zaznaczenie elementu w pierwszym polu listy wywołuje następującą obsługę zdarzeń. W tym przykładzie `Tasks` to zbiór `Task` obiektów. `Task` Klasa ma właściwość o nazwie `Priority`. Ta procedura obsługi zdarzeń uruchamia zapytanie LINQ, które zwraca kolekcję `Task` obiektów, które mają wartość priorytetu wybrane, a następnie zestawów, które jako <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 Drugie pole listy wiąże do tej kolekcji, ponieważ jego <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> wartość jest równa `{Binding}`. W wyniku zostanie zwrócona kolekcja (na podstawie `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Zobacz także
- [Udostępnianie danych do powiązania w XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
- [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Nowości w WPF w wersji 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
