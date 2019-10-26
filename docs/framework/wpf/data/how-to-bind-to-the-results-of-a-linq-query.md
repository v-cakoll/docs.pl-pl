---
title: Jak powiązać z wynikami zapytania LINQ
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 70f4b439d231d69e5671216bc4e62d0789ce66c7
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920137"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Jak powiązać z wynikami zapytania LINQ

W tym przykładzie pokazano, jak uruchomić zapytanie LINQ, a następnie powiązać z wynikami.

## <a name="example"></a>Przykład

Poniższy przykład tworzy dwa pola listy. Pierwsze pole listy zawiera trzy elementy listy.

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

Wybranie elementu z pierwszego pola listy powoduje wywołanie poniższego programu obsługi zdarzeń. W tym przykładzie `Tasks` jest kolekcją obiektów `Task`. Klasa `Task` ma właściwość o nazwie `Priority`. Ten program obsługi zdarzeń uruchamia zapytanie LINQ, które zwraca kolekcję `Task` obiektów, które mają wybraną wartość priorytetu, a następnie ustawia ten element jako <xref:System.Windows.FrameworkElement.DataContext%2A>:

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

Drugie pole listy tworzy powiązanie z tą kolekcją, ponieważ jej wartość <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jest ustawiona na `{Binding}`. W efekcie zostanie wyświetlona zwracana kolekcja (oparta na `myTaskTemplate` <xref:System.Windows.DataTemplate>).

## <a name="see-also"></a>Zobacz także

- [Udostępnianie danych do powiązania w XAML](how-to-make-data-available-for-binding-in-xaml.md)
- [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Nowości w WPF w wersji 4.5](../getting-started/whats-new.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
