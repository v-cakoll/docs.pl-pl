---
title: Pola ogólne i metody SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 310eb3ccecc3159234ed362ed044be7ad704dde4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634836"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Pola ogólne i metody SetField (LINQ to DataSet)
LINQ to DataSet dostarcza metody rozszerzające do klasy <xref:System.Data.DataRow> w celu uzyskania dostępu do wartości kolumn: Metoda <xref:System.Data.DataRowExtensions.Field%2A> i Metoda <xref:System.Data.DataRowExtensions.SetField%2A>. Te metody zapewniają łatwiejszy dostęp do wartości kolumn dla deweloperów, szczególnie w odniesieniu do wartości null. <xref:System.Data.DataSet> używa <xref:System.DBNull.Value?displayProperty=nameWithType> do reprezentowania wartości null, natomiast LINQ używa typów <xref:System.Nullable> i <xref:System.Nullable%601>. Użycie metody dostępu do istniejącej kolumny w <xref:System.Data.DataRow> wymaga rzutowania obiektu zwrotnego na odpowiedni typ. Jeśli określone pole w <xref:System.Data.DataRow> może mieć wartość null, należy jawnie sprawdzić pod kątem wartości null, ponieważ zwracają <xref:System.DBNull.Value?displayProperty=nameWithType> i niejawnie Rzutowanie na inny typ zgłasza <xref:System.InvalidCastException>. W poniższym przykładzie, jeśli metoda <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> nie była używana do sprawdzania wartości null, wyjątek zostałby wygenerowany, jeśli indeksator zwrócił <xref:System.DBNull.Value?displayProperty=nameWithType> i próbował rzutować go na <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> zapewnia dostęp do wartości kolumn <xref:System.Data.DataRow> i <xref:System.Data.DataRowExtensions.SetField%2A> ustawia wartości kolumn w <xref:System.Data.DataRow>. Metody <xref:System.Data.DataRowExtensions.Field%2A> i <xref:System.Data.DataRowExtensions.SetField%2A> obsługują Typy dopuszczające wartość null, więc nie trzeba jawnie sprawdzać wartości null tak jak w poprzednim przykładzie. Obie metody są metodami ogólnymi, więc nie trzeba rzutować zwracanego typu.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Należy zauważyć, że typ danych określony w parametrze ogólnym `T` metody <xref:System.Data.DataRowExtensions.Field%2A> i Metoda <xref:System.Data.DataRowExtensions.SetField%2A> musi być zgodna z typem podstawowej wartości. W przeciwnym razie zostanie wygenerowany wyjątek <xref:System.InvalidCastException>. Określona nazwa kolumny musi być również zgodna z nazwą kolumny w <xref:System.Data.DataSet>lub zostanie wygenerowane <xref:System.ArgumentException>. W obu przypadkach wyjątek jest zgłaszany w czasie wykonywania podczas wyliczania danych podczas wykonywania zapytania.  
  
 Sama metoda <xref:System.Data.DataRowExtensions.SetField%2A> nie wykonuje żadnych konwersji typów. Nie oznacza to jednak, że konwersja typu nie zostanie wykonana. Metoda <xref:System.Data.DataRowExtensions.SetField%2A> uwidacznia zachowanie ADO.NET klasy <xref:System.Data.DataRow>. Konwersja typu może być wykonywana przez obiekt <xref:System.Data.DataRow> i przekonwertowana wartość zostałaby następnie zapisana w obiekcie <xref:System.Data.DataRow>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRowExtensions>
