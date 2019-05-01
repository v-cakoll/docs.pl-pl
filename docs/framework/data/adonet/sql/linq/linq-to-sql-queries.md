---
title: Zapytania LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 49106502dc58eef36ea0c910c627c9cf397f419e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902879"
---
# <a name="linq-to-sql-queries"></a>Zapytania LINQ to SQL
Należy zdefiniować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytań przy użyciu tej samej składni, tak jak w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jedyna różnica polega na tym, że obiekty, do którego odwołuje się zapytania są mapowane do elementów w bazie danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada zapytania, który zapisane na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia. W szczególności aplikacja używa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsu API w celu wykonywania zapytania żądania. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostawcy następnie przekształca zapytania w tekstu SQL i wykonywania do dostawcy ADO deleguje odpowiednie uprawnienia. Dostawca ADO zwraca wyniki kwerendy w postaci `DataReader`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostawca tłumaczy wyniki ADO <xref:System.Linq.IQueryable> kolekcję obiektów użytkownika.  
  
> [!NOTE]
>  Większość metod i operatory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wbudowane typy mają bezpośredniego tłumaczeń do bazy danych SQL. Te, które [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] nie może dokonywać translacji generowanie wyjątków w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 W poniższej tabeli przedstawiono podobieństwa i różnice między [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania elementów.  
  
|Element|Zapytania LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Query|  
|----------|----------------|----------------------------------------------------------------------|  
|Zwracany typ zmiennej lokalnej, która przechowuje zapytanie (dla zapytań, które zwracają sekwencje)|Ogólny `IEnumerable`|Ogólny `IQueryable`|  
|Określanie źródła danych|Używa `From` (Visual Basic) lub `from` (C#) — klauzula|Ten sam|  
|Filtrowanie|Używa `Where` / `where` — klauzula|Ten sam|  
|Grupowanie|Używa `Group…By` / `groupby` — klauzula|Ten sam|  
|Wybieranie (projekcji)|Używa `Select` / `select` — klauzula|Ten sam|  
|Odroczone a natychmiastowe wykonanie|Zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Ten sam|  
|Implementowanie sprzężenia|Używa `Join` / `join` — klauzula|Można użyć `Join` / `join` klauzuli, ale bardziej efektywnie wykorzystuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [zapytań w relacjach](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Zdalne i lokalne wykonanie||Aby uzyskać więcej informacji, zobacz [zdalnego programu vs. Wykonanie lokalne](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Przesyłanie strumieniowe w stosunku do pamięci podręcznej zapytań|Nieobsługiwane w przypadku pamięci lokalnej||  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Podstawowe operacje zapytań LINQ](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relacje typów w operacjach zapytań LINQ](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
