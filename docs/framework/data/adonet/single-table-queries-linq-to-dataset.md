---
title: Kwerendy pojedynczej tabeli (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 1f4462f617eb81d30f893b52bdc674e1eee8961c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634771"
---
# <a name="single-table-queries-linq-to-dataset"></a>Kwerendy pojedynczej tabeli (LINQ to DataSet)
Zapytania dotyczące języka (LINQ) są używane w źródłach danych, które implementują interfejs <xref:System.Collections.Generic.IEnumerable%601> lub interfejs <xref:System.Linq.IQueryable%601>. Klasa <xref:System.Data.DataTable> nie implementuje żadnego interfejsu, dlatego należy wywołać metodę <xref:System.Data.DataTableExtensions.AsEnumerable%2A>, jeśli chcesz użyć <xref:System.Data.DataTable> jako źródła w klauzuli `From` zapytania LINQ.  
  
 Poniższy przykład pobiera wszystkie zamówienia online z tabeli SalesOrderHeader i wyświetla identyfikator zamówienia, datę zamówienia i numer zamówienia w konsoli programu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Zapytanie zmiennej lokalnej jest inicjowane z wyrażeniem zapytania, które działa na co najmniej jednym źródle informacji przez zastosowanie co najmniej jednego operatora zapytań z standardowych operatorów zapytań lub, w przypadku LINQ to DataSet, operatorów specyficznych dla klasy <xref:System.Data.DataSet>. W wyrażeniu zapytania w poprzednim przykładzie użyto dwóch standardowych operatorów zapytań: `Where` i `Select`.  
  
 Klauzula `Where` filtruje sekwencję w oparciu o warunek, w tym przypadku `OnlineOrderFlag` jest ustawiona na `true`. Operator `Select` przydziela i zwraca wyliczalny obiekt, który przechwytuje argumenty przekazane do operatora. W tym przykładzie typ anonimowy jest tworzony z trzema właściwościami: `SalesOrderID`, `OrderDate`i `SalesOrderNumber`. Wartości tych trzech właściwości są ustawiane na wartości kolumn `SalesOrderID`, `OrderDate`i `SalesOrderNumber` z tabeli `SalesOrderHeader`.  
  
 Pętla `foreach` następnie wylicza wyliczalny obiekt zwracany przez `Select` i daje wyniki zapytania. Ponieważ zapytanie jest typu <xref:System.Linq.Enumerable>, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, obliczanie zapytania jest odroczone do momentu powtarzania zmiennej zapytania przy użyciu pętli `foreach`. Wywnioskowana Ocena zapytania umożliwia przechowywanie zapytań jako wartości, które mogą być oceniane wiele razy, za każdym razem, gdy dają one inne wyniki.  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> zapewnia dostęp do wartości kolumn <xref:System.Data.DataRow> i <xref:System.Data.DataRowExtensions.SetField%2A> (niepokazywany w poprzednim przykładzie) ustawia wartości kolumn w <xref:System.Data.DataRow>. Metody <xref:System.Data.DataRowExtensions.Field%2A> i <xref:System.Data.DataRowExtensions.SetField%2A> obsługują Typy dopuszczające wartość null, więc nie trzeba jawnie sprawdzać wartości null. Obie metody są metodami ogólnymi, co oznacza, że nie trzeba rzutować zwracanego typu. Można użyć metody dostępu do istniejącej kolumny w <xref:System.Data.DataRow> (na przykład `o["OrderDate"]`), ale wykonanie tej operacji wymagałoby rzutowania obiektu powrotnego na odpowiedni typ.  Jeśli kolumna dopuszcza wartość null, należy sprawdzić, czy wartość jest równa null za pomocą metody <xref:System.Data.DataRow.IsNull%2A>. Aby uzyskać więcej informacji, zobacz [pola ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Należy zauważyć, że typ danych określony w `T` parametru generycznego metody <xref:System.Data.DataRowExtensions.Field%2A> i metody <xref:System.Data.DataRowExtensions.SetField%2A> musi być zgodny z typem podstawowej wartości lub zostanie wygenerowany <xref:System.InvalidCastException>. Określona nazwa kolumny musi być również zgodna z nazwą kolumny w <xref:System.Data.DataSet> lub zostanie wygenerowane <xref:System.ArgumentException>. W obu przypadkach wyjątek jest generowany podczas wyliczania danych w czasie wykonywania, gdy zapytanie jest wykonywane.  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania wielotabelowe](cross-table-queries-linq-to-dataset.md)
- [Wykonywanie zapytania do typizowanych zestawów danych](querying-typed-datasets.md)
- [Pole ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
