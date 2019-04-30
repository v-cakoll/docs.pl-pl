---
title: Zapytania Jednotabelowe (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 00b0773ba66ad8e0acfdccb37964030a9cacff52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664171"
---
# <a name="single-table-queries-linq-to-dataset"></a>Zapytania Jednotabelowe (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] zapytania pracować nad źródeł danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. <xref:System.Data.DataTable> Klasa nie implementuje albo interfejsu, więc należy wywołać <xref:System.Data.DataTableExtensions.AsEnumerable%2A> metody, jeśli chcesz użyć <xref:System.Data.DataTable> jako źródło w `From` klauzuli [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania.  
  
 Poniższy przykład pobiera wszystkie zamówienia online z tabeli SalesOrderHeader i generuje identyfikator zamówienia, Data zamówienia i numer zamówienia w konsoli.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Lokalnej zmiennej zapytania jest inicjowany przy użyciu wyrażenie zapytania, który działa na co najmniej jedno źródło informacji poprzez zastosowanie jednego lub więcej operatorów zapytań, z poziomu standardowych operatorów zapytań, albo w przypadku [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], operatory specyficzne dla <xref:System.Data.DataSet>klasy. Wyrażenia zapytania w poprzednim przykładzie korzysta z dwóch standardowych operatorów zapytań: `Where` i `Select`.  
  
 `Where` Klauzuli filtry sekwencji na podstawie warunku, w tym przypadku `OnlineOrderFlag` ustawiono `true`. `Select` Operator przydzielało i zwracało obiekt wyliczalny, który przechwytuje Argumenty przekazane do operatora. W tym powyżej przykładzie typu anonimowego jest tworzony przy użyciu trzech właściwości: `SalesOrderID`, `OrderDate`, i `SalesOrderNumber`. Wartości te trzy właściwości są ustawione na wartości `SalesOrderID`, `OrderDate`, i `SalesOrderNumber` kolumny z `SalesOrderHeader` tabeli.  
  
 `foreach` Pętli jest następnie wylicza wyliczalny obiektu zwróconego przez `Select` i daje wyniki zapytania. Ponieważ zapytanie jest <xref:System.Linq.Enumerable> typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, oceny zapytania jest odroczone do czasu zmienna zapytania jest iterowana przy użyciu `foreach` pętli. Odroczone zapytanie pozwala zapytania, które mają być przechowywane jako wartości, które mogą być obliczane wiele razy, każdorazowo reaguje potencjalnie różne wyniki.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda zapewnia dostęp do wartości kolumny <xref:System.Data.DataRow> i <xref:System.Data.DataRowExtensions.SetField%2A> (niewyświetlany w poprzednim przykładzie) ustawia wartości kolumn w <xref:System.Data.DataRow>. Zarówno <xref:System.Data.DataRowExtensions.Field%2A> metody i <xref:System.Data.DataRowExtensions.SetField%2A> metody obsługi typów dopuszczających wartości zerowe, dzięki czemu nie trzeba jawnie szukać wartości null. Obie metody są metod rodzajowych także, co oznacza, że będą musieli rzutować zwracany typ. Można użyć istniejącego metody dostępu do kolumny w <xref:System.Data.DataRow> (na przykład `o["OrderDate"]`), ale spowoduje to więc wymagają rzutować zwracany obiekt do odpowiedniego typu.  Jeśli kolumna ma wartość null musisz zaznaczyć, jeśli ma wartość null przy użyciu <xref:System.Data.DataRow.IsNull%2A> metody. Aby uzyskać więcej informacji, zobacz [pole ogólne i metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Należy zauważyć, że typ danych określony przez parametr ogólny `T` z <xref:System.Data.DataRowExtensions.Field%2A> metody i <xref:System.Data.DataRowExtensions.SetField%2A> metoda musi odpowiadać typowi podstawowej wartości lub <xref:System.InvalidCastException> zostanie zgłoszony. Określona nazwa kolumny musi być również zgodna nazwa kolumny w <xref:System.Data.DataSet> lub <xref:System.ArgumentException> zostanie zgłoszony. W obu przypadkach wyjątek jest generowany na wyliczenie danych w czasie wykonywania, podczas wykonywania zapytania.  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania wielotabelowe](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Wykonywanie zapytania do typizowanych zestawów danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Pole ogólne i metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
