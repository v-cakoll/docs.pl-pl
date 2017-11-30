---
title: Pojedynczej tabeli zapytania (LINQ do DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f157bb172d173872aa7b792035b653976a9c1c0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="single-table-queries-linq-to-dataset"></a>Pojedynczej tabeli zapytania (LINQ do DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]zapytania działają w źródeł danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. <xref:System.Data.DataTable> Klasa nie implementuje albo interfejsu, dlatego należy wywołać <xref:System.Data.DataTableExtensions.AsEnumerable%2A> metodę, jeśli chcesz użyć <xref:System.Data.DataTable> jako źródło w `From` klauzuli [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania.  
  
 W poniższym przykładzie pobiera zamówień online z tabeli SalesOrderHeader i generuje identyfikator zamówienia, Data zamówienia i numer zamówienia do konsoli.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Zapytanie zmiennej lokalnej jest inicjowana z wyrażenia zapytania, który działa na co najmniej jedno źródło informacji poprzez zastosowanie co najmniej jeden operatorów zapytań przy użyciu dowolnego standardowych operatorów zapytań, lub w przypadku [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], Operatorzy specyficzne dla <xref:System.Data.DataSet>klasy. Wyrażenia zapytania w poprzednim przykładzie używa dwóch standardowych operatorów zapytań: `Where` i `Select`.  
  
 `Where` Klauzuli filtruje sekwencji na podstawie warunku, w tym przypadku `OnlineOrderFlag` ma ustawioną wartość `true`. `Select` Operator przydziela i zwraca obiekt wyliczalny, który przechwytuje Argumenty przekazane do operatora. W tym powyżej przykład typu anonimowego jest tworzony z trzy właściwości: `SalesOrderID`, `OrderDate`, i `SalesOrderNumber`. Wartości te trzy właściwości są ustawiane na wartości `SalesOrderID`, `OrderDate`, i `SalesOrderNumber` kolumny z `SalesOrderHeader` tabeli.  
  
 `foreach` Pętli następnie wylicza obiektu wyliczalny, zwracane przez `Select` i zwraca wyniki zapytania. Ponieważ zapytanie jest <xref:System.Linq.Enumerable> typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>, oceny zapytania jest odłożona do zmiennej zapytania jest powtórzyć w przypadku `foreach` pętli. Pozwala zapytań, które mają być przechowywane jako wartości, które mogą być obliczane wiele razy, zawsze reaguje potencjalnie różne wyniki zapytań odroczonych.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda zapewnia dostęp do wartości kolumny <xref:System.Data.DataRow> i <xref:System.Data.DataRowExtensions.SetField%2A> (nie pokazana w poprzednim przykładzie) ustawia wartości w kolumnie w <xref:System.Data.DataRow>. Zarówno <xref:System.Data.DataRowExtensions.Field%2A> — metoda i <xref:System.Data.DataRowExtensions.SetField%2A> — metoda obsługi typów dopuszczających wartości zerowe, dzięki czemu nie trzeba jawnie sprawdziła wartości null. Obie metody metodami ogólny, również, co oznacza, że nie masz można rzutować typu zwracanego. Można użyć istniejącego akcesor kolumny w <xref:System.Data.DataRow> (na przykład `o["OrderDate"]`), ale to tak będzie wymagać zwracany obiekt do odpowiedniego typu rzutowania.  Jeśli kolumna ma wartość null należy sprawdzić, jeśli ma wartość null przy użyciu <xref:System.Data.DataRow.IsNull%2A> metody. Aby uzyskać więcej informacji, zobacz [ogólnego pól i metod SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Należy pamiętać, że typ danych określony w parametrze ogólnym `T` z <xref:System.Data.DataRowExtensions.Field%2A> — metoda i <xref:System.Data.DataRowExtensions.SetField%2A> metody musi odpowiadać typowi wartości podstawowej lub <xref:System.InvalidCastException> zostanie wygenerowany. Określona nazwa kolumny musi również zgodna z nazwą kolumny <xref:System.Data.DataSet> lub <xref:System.ArgumentException> zostanie wygenerowany. W obu przypadkach wyjątku w czasie wykonywania wyliczanie danych podczas wykonywania zapytania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w tabeli](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Wykonywanie zapytania Typizowane zbiory danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Pole ogólnego i metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
