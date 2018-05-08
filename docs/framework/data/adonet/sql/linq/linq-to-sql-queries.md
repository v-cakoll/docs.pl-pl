---
title: LINQ do SQL zapytań
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: ef761f696eaefd6daef9a32892e4c5356a178418
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-sql-queries"></a>LINQ do SQL zapytań
Należy zdefiniować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania przy użyciu takiej samej składni jak [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jedyna różnica polega na tym, że obiekty odwołuje się do zapytania są mapowane do elementów w bazie danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zapytania zostanie zapisany na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia. W szczególności, aplikacja używa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsu API do wykonywania zapytania żądania. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostawcy następnie przekształca zapytania w tekstu SQL i deleguje do dostawcy ADO wykonania. Dostawca ADO zwraca wyniki zapytania jako `DataReader`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostawca tłumaczy wyniki ADO w <xref:System.Linq.IQueryable> kolekcji obiektów użytkownika.  
  
> [!NOTE]
>  Większość metod i operatory w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] typy wbudowane mieć tłumaczeń bezpośrednio do bazy danych SQL. Te, które [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] nie może dokonywać translacji Generowanie wyjątki czasu wykonywania. Aby uzyskać więcej informacji, zobacz [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 W poniższej tabeli przedstawiono podobieństwa i różnice między [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania elementów.  
  
|Element|Zapytania LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zapytania|  
|----------|----------------|----------------------------------------------------------------------|  
|Zwracany typ zmiennej lokalnej, która przechowuje zapytania (w przypadku zapytań, które zwracają sekwencji)|Ogólny `IEnumerable`|Ogólny `IQueryable`|  
|Określanie źródła danych|Używa `From` (Visual Basic) lub `from` — klauzula (C#)|tym samym|  
|Filtrowanie|Używa `Where` / `where` — klauzula|tym samym|  
|Grupowanie|Używa `Group…By` / `groupby` — klauzula|tym samym|  
|Wybieranie (projekcji)|Używa `Select` / `select` — klauzula|tym samym|  
|Odroczone i natychmiastowego wykonania|Zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|tym samym|  
|Implementowanie sprzężeń|Używa `Join` / `join` — klauzula|Można użyć `Join` / `join` klauzuli, ale efektywniej używa <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [zapytań w relacji](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Zdalne i wykonanie lokalne||Aby uzyskać więcej informacji, zobacz [zdalnego programu vs. Wykonanie lokalne](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Przesyłanie strumieniowe i kwerendy w pamięci podręcznej|Nie ma zastosowania w przypadku scenariusza pamięci lokalnej||  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Podstawowe operacje zapytań LINQ](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 [Relacje typów w operacjach zapytań LINQ](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
