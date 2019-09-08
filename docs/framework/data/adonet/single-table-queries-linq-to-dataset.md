---
title: Kwerendy pojedynczej tabeli (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 8807125bd61c71217ca96f3b5a38148ed100073b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794365"
---
# <a name="single-table-queries-linq-to-dataset"></a>Kwerendy pojedynczej tabeli (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]zapytania pracują ze źródłami danych, <xref:System.Collections.Generic.IEnumerable%601> które implementują <xref:System.Linq.IQueryable%601> interfejs lub interfejs. <xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.AsEnumerable%2A> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] `From` Klasa nie implementuje żadnego interfejsu, dlatego należy wywołać metodę, jeśli chcesz użyć jako źródła w klauzuli zapytania. <xref:System.Data.DataTable>  
  
 Poniższy przykład pobiera wszystkie zamówienia online z tabeli SalesOrderHeader i wyświetla identyfikator zamówienia, datę zamówienia i numer zamówienia w konsoli programu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Zapytanie zmiennej lokalnej jest inicjowane z wyrażeniem zapytania, które działa na co najmniej jednym źródle informacji przez zastosowanie co najmniej jednego operatora zapytań z standardowych operatorów zapytań lub, w przypadku LINQ to DataSet, operatory specyficzne dla <xref:System.Data.DataSet>Klasa. W wyrażeniu zapytania w poprzednim przykładzie użyto dwóch standardowych operatorów zapytań: `Where` i. `Select`  
  
 Klauzula filtruje sekwencję w oparciu o warunek, w tym przypadku `OnlineOrderFlag` jest ustawiona na `true`. `Where` `Select` Operator przydziela i zwraca wyliczalny obiekt, który przechwytuje argumenty przekazane do operatora. W tym przykładzie typ anonimowy jest tworzony z trzema właściwościami: `SalesOrderID`, `OrderDate`, i `SalesOrderNumber`. Wartości tych trzech właściwości `SalesOrderID`są ustawiane na wartości, `OrderDate` `SalesOrderHeader` , i `SalesOrderNumber` kolumn z tabeli.  
  
 Pętla następnie wylicza wyliczalny obiekt zwracany przez `Select` i daje wyniki zapytania. `foreach` Ponieważ zapytanie jest <xref:System.Linq.Enumerable> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, obliczanie zapytania jest odroczone do momentu, gdy zmienna zapytania zostanie `foreach` powtórzona przy użyciu pętli. Wywnioskowana Ocena zapytania umożliwia przechowywanie zapytań jako wartości, które mogą być oceniane wiele razy, za każdym razem, gdy dają one inne wyniki.  
  
 Metoda zapewnia dostęp do wartości <xref:System.Data.DataRow> kolumn a i <xref:System.Data.DataRowExtensions.SetField%2A> (nie pokazano w <xref:System.Data.DataRow>poprzednim przykładzie) ustawia wartości kolumn w. <xref:System.Data.DataRowExtensions.Field%2A> <xref:System.Data.DataRowExtensions.Field%2A> Metody i<xref:System.Data.DataRowExtensions.SetField%2A> metody obsługują Typy dopuszczające wartość null, więc nie trzeba jawnie sprawdzać wartości null. Obie metody są metodami ogólnymi, co oznacza, że nie trzeba rzutować zwracanego typu. Można użyć metody dostępu <xref:System.Data.DataRow> do istniejącej kolumny (na `o["OrderDate"]`przykład), ale wykonanie tej operacji wymagałoby rzutowania obiektu powrotnego na odpowiedni typ.  Jeśli kolumna dopuszcza wartość null, należy sprawdzić, czy wartość jest równa null przy użyciu <xref:System.Data.DataRow.IsNull%2A> metody. Aby uzyskać więcej informacji, zobacz [pola ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Należy zauważyć, że typ danych określony w parametrze `T` <xref:System.Data.DataRowExtensions.Field%2A> ogólnym metody i <xref:System.Data.DataRowExtensions.SetField%2A> metody musi być zgodny <xref:System.InvalidCastException> z typem podstawowej wartości lub zostanie wygenerowany. Określona nazwa kolumny musi być również zgodna z nazwą kolumny w <xref:System.Data.DataSet> <xref:System.ArgumentException> lub zostanie wygenerowane. W obu przypadkach wyjątek jest generowany podczas wyliczania danych w czasie wykonywania, gdy zapytanie jest wykonywane.  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania wielotabelowe](cross-table-queries-linq-to-dataset.md)
- [Wykonywanie zapytania do typizowanych zestawów danych](querying-typed-datasets.md)
- [Pole ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
