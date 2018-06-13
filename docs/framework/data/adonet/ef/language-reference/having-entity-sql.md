---
title: O (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 75f30c19fb54d66be0e460ab64b61d283d650005
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764388"
---
# <a name="having-entity-sql"></a>O (jednostka SQL)
Określa warunek wyszukiwania dla grupy lub agregacja.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `search_condition`  
 Określa warunek wyszukiwania dla grupy lub agregacji spełnić. Klauzula HAVING HAVING jest używana z GROUP BY ALL, zastępuje wszystkie.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula HAVING pozwala określić dodatkowy warunek filtrowania wyniku grupowanie. Jeśli nie określono żadnych klauzuli GROUP BY w wyrażeniu zapytania, przyjmowana jest niejawne grupy jednego zestawu.  
  
> [!NOTE]
>  HAVING może być używany tylko z [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji. Gdy [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) jest nieużywane, HAVING zachowuje się jak klauzuli WHERE.  
  
 Klauzula HAVING działa jak w klauzuli WHERE, z tą różnicą, że jest stosowana po wykonaniu operacji GROUP BY. Oznacza to, że w klauzuli HAVING można tylko odwołuje się do grupowania aliasy i wartościami zagregowanymi, jak pokazano w poniższym przykładzie.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Poprzedni ogranicza grupy tylko do tych zawierających więcej niż jeden produkt.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatory HAVING i GROUP BY do określania warunku wyszukiwania dla grupy lub agregacja. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
