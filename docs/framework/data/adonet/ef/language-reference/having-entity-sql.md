---
title: POSIADANIE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 97ed6e06241804bf2f576c910a2235b0cb570bbb
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833732"
---
# <a name="having-entity-sql"></a>POSIADANIE (Entity SQL)
Określa warunek wyszukiwania dla grupy lub agregacji.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `search_condition`  
 Określa warunek wyszukiwania dla grupy lub agregacji, które mają zostać spełnione. Gdy jest używany z klauzulą GROUP BY ALL, klauzula HAVING zastępuje wszystkie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula HAVING służy do określania dodatkowego warunku filtrowania w wyniku grupowania. Jeśli w wyrażeniu zapytania nie określono klauzuli GROUP BY, założono niejawną grupę z pojedynczym zestawem.  
  
> [!NOTE]
> HAVING można używać tylko z instrukcją [SELECT](select-entity-sql.md) . Gdy klauzula [Group by](group-by-entity-sql.md) nie jest używana, zachowanie jest podobne do klauzuli WHERE.  
  
Klauzula HAVING działa podobnie jak klauzula WHERE, z tą różnicą, że jest stosowana po operacji Grupuj według. Oznacza to, że klauzula HAVING może tylko tworzyć odwołania do aliasów grupowania i agregacji, jak pokazano w następującym przykładzie:
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Poprzednie ogranicza grupy tylko do tych, które zawierają więcej niż jeden produkt.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatorów HAVING i GROUP BY, aby określić warunek wyszukiwania dla grupy lub agregacji. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Wyrażenia zapytania](query-expressions-entity-sql.md)
