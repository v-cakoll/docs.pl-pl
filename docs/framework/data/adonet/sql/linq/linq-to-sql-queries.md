---
title: Zapytania LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 478138d26d6cdf656b2487c637a5eb13784126e9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634383"
---
# <a name="linq-to-sql-queries"></a>Zapytania LINQ to SQL
Należy zdefiniować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytań przy użyciu takiej samej składni jak w LINQ. Jedyną różnicą jest to, że obiekty, do których odwołują się zapytania, są mapowane na elementy w bazie danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zapytania zapisane w równoważne zapytania SQL i wysyła je do serwera w celu przetworzenia. Dokładniej mówiąc, aplikacja używa interfejsu API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aby zażądać wykonania zapytania. Dostawca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] następnie przekształca zapytanie w tekst SQL i deleguje wykonywanie do dostawcy ADO. Dostawca ADO zwraca wyniki zapytania jako `DataReader`. Dostawca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy wyniki ADO do <xref:System.Linq.IQueryable> kolekcji obiektów użytkownika.  
  
> [!NOTE]
> Większość metod i operatorów na .NET Framework typów wbudowanych ma bezpośrednie tłumaczenia na SQL. Te, które nie mogą przetłumaczyć generowania wyjątków czasu wykonywania. Aby uzyskać więcej informacji, zobacz [Mapowanie typu SQL-CLR](sql-clr-type-mapping.md).  
  
 W poniższej tabeli przedstawiono podobieństwa i różnice między elementami zapytania LINQ i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Element|Zapytanie LINQ|Zapytanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]|  
|----------|----------------|----------------------------------------------------------------------|  
|Zwracany typ zmiennej lokalnej, która przechowuje zapytanie (dla zapytań, które zwracają sekwencje)|`IEnumerable` ogólny|`IQueryable` ogólny|  
|Określanie źródła danych|Używa klauzuli `From` (Visual Basic) lub `from` (C#)|Ten|  
|Filtrowanie|Używa klauzuli `Where`/`where`|Ten|  
|Grupowanie|Używa klauzuli `Group…By`/`groupby`|Ten|  
|Zaznaczanie (Projekcja)|Używa klauzuli `Select`/`select`|Ten|  
|Odroczone względem natychmiastowego wykonania|Zobacz [wprowadzenie do zapytań LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Ten|  
|Implementowanie sprzężeń|Używa klauzuli `Join`/`join`|Można użyć klauzuli `Join`/`join`, ale bardziej efektywnie używa atrybutu <xref:System.Data.Linq.Mapping.AssociationAttribute>. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań w relacjach](querying-across-relationships.md).|  
|Zdalne a wykonywanie lokalne||Aby uzyskać więcej informacji, zobacz [zdalne a wykonywanie lokalne](remote-vs-local-execution.md).|  
|Przesyłanie strumieniowe i wykonywanie zapytań w pamięci podręcznej|Nie dotyczy w przypadku lokalnego scenariusza pamięci||  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do zapytań LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Podstawowe operacje zapytań LINQ](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relacje typów w operacjach zapytań LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Pojęcia dotyczące zapytań](query-concepts.md)
