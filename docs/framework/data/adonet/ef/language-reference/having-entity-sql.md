---
title: POSIADANIE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: fe8a177b83932c1c7607f8444c05292c0ee29684
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250851"
---
# <a name="having-entity-sql"></a>POSIADANIE (Entity SQL)
Określa warunek wyszukiwania dla grupy lub agregacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `search_condition`  
 Określa warunek wyszukiwania dla grupy lub agregacji, które mają zostać spełnione. Gdy jest używany z klauzulą GROUP BY ALL, klauzula HAVING zastępuje wszystkie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula HAVING służy do określania dodatkowego warunku filtrowania w wyniku grupowania. Jeśli w wyrażeniu zapytania nie określono klauzuli GROUP BY, założono niejawną grupę z pojedynczym zestawem.  
  
> [!NOTE]
> HAVING można używać tylko z instrukcją [SELECT](select-entity-sql.md) . Gdy klauzula [Group by](group-by-entity-sql.md) nie jest używana, zachowanie jest podobne do klauzuli WHERE.  
  
 Klauzula HAVING działa podobnie jak klauzula WHERE, z tą różnicą, że jest stosowana po operacji Grupuj według. Oznacza to, że klauzula HAVING może tylko tworzyć odwołania do aliasów grupowania i agregacji, jak pokazano w poniższym przykładzie.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Poprzednie ogranicza grupy tylko do tych, które zawierają więcej niż jeden produkt.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatorów HAVING i GROUP BY, aby określić warunek wyszukiwania dla grupy lub agregacji. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Wyrażenia zapytania](query-expressions-entity-sql.md)
