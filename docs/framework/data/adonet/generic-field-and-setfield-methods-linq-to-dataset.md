---
title: Pole ogólne i metody SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 69f5489d82511c249c1bde3ab65429561a87af59
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307276"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Pole ogólne i metody SetField (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] udostępnia metody rozszerzenia dla <xref:System.Data.DataRow> klasy do uzyskiwania dostępu do wartości kolumny: <xref:System.Data.DataRowExtensions.Field%2A> metody i <xref:System.Data.DataRowExtensions.SetField%2A> metody. Te metody zapewnienia łatwiejszego dostępu do wartości w kolumnie dla deweloperów, szczególnie w odniesieniu do wartości null. <xref:System.Data.DataSet> Używa <xref:System.DBNull.Value> do reprezentowania wartości null, podczas gdy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] używa obsługi typu dopuszczającego wartość null, wprowadzona w [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Przy użyciu istniejących metody dostępu do kolumny w <xref:System.Data.DataRow> wymaga rzutować zwracany obiekt do odpowiedniego typu. Jeśli określonego pola w <xref:System.Data.DataRow> może mieć wartość null, musi jawnie sprawdzenie, czy wartość null, ponieważ zwracanie <xref:System.DBNull.Value> i niejawnie rzutowania go na inny typ zgłasza <xref:System.InvalidCastException>. W poniższym przykładzie Jeśli <xref:System.Data.DataRow.IsNull%2A> metoda nie została użyta pod kątem wartości null, jeśli zwrócony przez indeksator będzie zgłoszony wyjątek <xref:System.DBNull.Value> próbuję rzutować go na <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda zapewnia dostęp do wartości kolumny <xref:System.Data.DataRow> i <xref:System.Data.DataRowExtensions.SetField%2A> ustawia wartości kolumn w <xref:System.Data.DataRow>. Zarówno <xref:System.Data.DataRowExtensions.Field%2A> metody i <xref:System.Data.DataRowExtensions.SetField%2A> metody obsługi typów dopuszczających wartości zerowe, dzięki czemu nie trzeba jawnie szukać wartości null, co w poprzednim przykładzie. Obie metody są metody rodzajowe również, aby nie musieli rzutować zwracany typ.  
  
 W poniższym przykładzie użyto <xref:System.Data.DataRowExtensions.Field%2A> metody.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Należy zauważyć, że typ danych określony przez parametr ogólny `T` z <xref:System.Data.DataRowExtensions.Field%2A> metody i <xref:System.Data.DataRowExtensions.SetField%2A> metoda musi odpowiadać typowi podstawowej wartości. W przeciwnym razie <xref:System.InvalidCastException> zostanie zgłoszony wyjątek. Określona nazwa kolumny musi być również zgodna nazwa kolumny w <xref:System.Data.DataSet>, lub <xref:System.ArgumentException> zostanie zgłoszony. W obu przypadkach wyjątku w czasie wykonywania podczas wyliczania dane podczas wykonywania zapytania.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Sama metoda nie wykonuje żadnych konwersji typu. Nie oznacza to, jednak nie nastąpi konwersji typu. <xref:System.Data.DataRowExtensions.SetField%2A> Metoda udostępnia zachowanie ADO.NET <xref:System.Data.DataRow> klasy. Konwersja typu może zostać wykonana przez <xref:System.Data.DataRow> obiektu i przekonwertowana wartości następnie zostaną zapisane w <xref:System.Data.DataRow> obiektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRowExtensions>
