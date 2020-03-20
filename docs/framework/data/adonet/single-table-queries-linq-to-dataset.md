---
title: Kwerendy jednostołowe (LINQ do DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 7bb8d8e19ac9cf36eabc061ceba9c649b8a4cc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148975"
---
# <a name="single-table-queries-linq-to-dataset"></a>Kwerendy jednostołowe (LINQ do DataSet)
Zapytania zintegrowane z językiem (LINQ) działają na <xref:System.Collections.Generic.IEnumerable%601> źródłach <xref:System.Linq.IQueryable%601> danych, które implementują interfejs lub interfejs. Klasa <xref:System.Data.DataTable> nie implementuje żadnego interfejsu, więc <xref:System.Data.DataTableExtensions.AsEnumerable%2A> należy wywołać metodę, jeśli chcesz użyć <xref:System.Data.DataTable> jako źródło w `From` klauzuli kwerendy LINQ.  
  
 Poniższy przykład pobiera wszystkie zamówienia online z SalesOrderHeader tabeli i wyprowadza identyfikator zamówienia, datę zamówienia i numer zamówienia do konsoli.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
 Kwerenda zmiennej lokalnej jest inicjowana za pomocą wyrażenia kwerendy, które działa na co najmniej jednym źródle informacji, stosując jeden lub więcej operatorów <xref:System.Data.DataSet> zapytań z operatorów zapytań standardowych lub, w przypadku LINQ do DataSet, operatorów specyficznych dla tej klasy. Wyrażenie kwerendy w poprzednim przykładzie używa dwóch `Where` standardowych `Select`operatorów zapytań: i .  
  
 Klauzula `Where` filtruje sekwencję na podstawie warunku, w tym przypadku, że jest ustawiona `OnlineOrderFlag` na `true`. Operator `Select` przydziela i zwraca wyliczalny obiekt, który przechwytuje argumenty przekazywane do operatora. W tym powyższym przykładzie tworzony jest typ `SalesOrderID` `OrderDate`anonimowy `SalesOrderNumber`z trzema właściwościami: , , i . Wartości tych trzech właściwości są ustawiane na `SalesOrderID` `OrderDate`wartości `SalesOrderNumber` , i `SalesOrderHeader` kolumny z tabeli.  
  
 Pętla `foreach` następnie wylicza wyliczany `Select` obiekt wyliczany przez i daje wyniki kwerendy. Ponieważ kwerenda <xref:System.Linq.Enumerable> jest typem, który implementuje, <xref:System.Collections.Generic.IEnumerable%601>ocena kwerendy jest odroczona, dopóki `foreach` zmienna kwerendy nie zostanie przesuń iterowana przy użyciu pętli. Odroczona ocena kwerendy umożliwia kwerendy, które mają być przechowywane jako wartości, które mogą być oceniane wiele razy, za każdym razem dając potencjalnie różne wyniki.  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> zapewnia dostęp do wartości <xref:System.Data.DataRow> kolumn <xref:System.Data.DataRowExtensions.SetField%2A> a i (nie pokazano w poprzednim <xref:System.Data.DataRow>przykładzie) ustawia wartości kolumn w . Zarówno <xref:System.Data.DataRowExtensions.Field%2A> metoda, <xref:System.Data.DataRowExtensions.SetField%2A> jak i metoda obsługują typy nullable, więc nie trzeba jawnie sprawdzić wartości null. Obie metody są również metody ogólne, co oznacza, że nie trzeba rzutować typu zwracany. Można użyć istniejącego akcesora kolumny <xref:System.Data.DataRow> `o["OrderDate"]`w (na przykład ), ale w ten sposób wymagałoby to rzutowania obiektu zwracany do odpowiedniego typu.  Jeśli kolumna jest nullable trzeba sprawdzić, czy wartość <xref:System.Data.DataRow.IsNull%2A> jest null przy użyciu metody. Aby uzyskać więcej informacji, zobacz [Ogólne pola i Metody Pola Zestawu](generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Należy zauważyć, że typ danych `T` określony <xref:System.Data.DataRowExtensions.Field%2A> w <xref:System.Data.DataRowExtensions.SetField%2A> parametrze ogólnym metody i metody <xref:System.InvalidCastException> musi odpowiadać typowi wartości podstawowej lub zostanie zgłoszony. Określona nazwa kolumny musi również odpowiadać <xref:System.Data.DataSet> nazwie <xref:System.ArgumentException> kolumny w lub zostanie rzucona. W obu przypadkach wyjątek jest generowany w czasie wykonywania wyliczenia danych podczas wykonywania kwerendy.  
  
## <a name="see-also"></a>Zobacz też

- [Zapytania wielotabelowe](cross-table-queries-linq-to-dataset.md)
- [Wykonywanie zapytania do typizowanych zestawów danych](querying-typed-datasets.md)
- [Pole ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
