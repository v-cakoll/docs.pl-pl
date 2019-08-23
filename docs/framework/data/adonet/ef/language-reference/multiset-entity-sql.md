---
title: Zestaw WIELOKROTNy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: eb676feeb168e1fb184f3869a18e138bff34211b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929347"
---
# <a name="multiset-entity-sql"></a>Zestaw WIELOKROTNy (Entity SQL)
Tworzy wystąpienie zestawu wielokrotnego z listy wartości. Wszystkie wartości w konstruktorze zestawów wielokrotnych muszą być zgodne z typem `T`. Puste konstruktory wielu zestawów są niedozwolone.  
  
## <a name="syntax"></a>Składnia  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolna prawidłowa lista wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja typu zestaw wielokrotny\<T >.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]oferuje trzy rodzaje konstruktorów: konstruktory wierszy, konstruktory obiektów i konstruktory wielokrotnego (lub kolekcji). Aby uzyskać więcej informacji, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Konstruktor zestawów wielokrotnych tworzy wystąpienie zestawu wielokrotnego z listy wartości. Wszystkie wartości w konstruktorze muszą być zgodnego typu.  
  
 Na przykład następujące wyrażenie tworzy zestaw wielokrotny dla liczb całkowitych.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> Zagnieżdżone literały zestawu wielokrotnego są obsługiwane tylko wtedy, gdy zestaw wielokrotny zawijania zawiera pojedynczy element wielokrotnego zestawu. na przykład `{{1, 2, 3}}`. Gdy zestaw wielokrotny zawijania ma wiele elementów wielokrotnych ( `{{1, 2}, {3, 4}}`na przykład), zagnieżdżone literały zestawów wielokrotnych nie są obsługiwane.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora WIELOKROTNego tworzenia wystąpienia zestawu wielokrotnego na podstawie listy wartości. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Zobacz także

- [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
