---
title: POSIADANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 7b147a84a43677afa53f7872f8042f1cf44137cf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316183"
---
# <a name="having-entity-sql"></a>POSIADANIE (jednostka SQL)
Określa warunek wyszukiwania dla grupy lub agregacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `search_condition`  
 Określa warunek wyszukiwania określający grupę lub agregacji spełnić. W klauzuli HAVING HAVING jest używany z GROUP BY ALL, zastępuje wszystkie.  
  
## <a name="remarks"></a>Uwagi  
 W klauzuli HAVING pozwala określić dodatkowy warunek filtrowania wynik grupowanie. W przypadku braku klauzuli GROUP BY jest określona w wyrażeniu zapytania, przyjmowana jest niejawne grupy jednego zestawu.  
  
> [!NOTE]
>  HAVING mogą być używane tylko z [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji. Gdy [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) jest nie używane HAVING zachowuje się jak klauzuli WHERE.  
  
 W klauzuli HAVING działa jak klauzuli WHERE, chyba że zostanie zastosowane po wykonaniu operacji GROUP BY. Oznacza to, że w klauzuli HAVING można tylko odwołuje się do grupowania aliasów i agregacji, jak pokazano w poniższym przykładzie.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Poprzedni ogranicza grupy tylko do tych, które zawierają więcej niż jeden produkt.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatorów HAVING i GROUP BY w celu określenia warunku wyszukiwania dla grupy lub agregacji. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Wyrażenia kwerend](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
