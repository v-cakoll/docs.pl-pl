---
title: MULTISET (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: ad54450b8f987da9a7a502d6561a58794a24b207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655182"
---
# <a name="multiset-entity-sql"></a>MULTISET (jednostka SQL)
Tworzy wystąpienie zestawu wielokrotnego na podstawie listy wartości. Wszystkie wartości w Konstruktor MULTISET musi być zgodne z typem `T`. Pusty zestaw wielokrotny konstruktory nie są dozwolone.  
  
## <a name="syntax"></a>Składnia  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wszystkie prawidłowe listy wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja typu MULTISET\<T >.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zawiera trzy rodzaje konstruktorów: wiersz konstruktorów, obiektu konstruktorów i konstruktorów multiset (lub kolekcji). Aby uzyskać więcej informacji, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Konstruktor multiset tworzy wystąpienie zestawu wielokrotnego na podstawie listy wartości. Wszystkie wartości w Konstruktorze musi być zgodne z typem.  
  
 Na przykład poniższe wyrażenie tworzy zestaw wielokrotny liczb całkowitych.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  Zagnieżdżone literały zestawów wielokrotnych są obsługiwana tylko w przypadku multiset zawijania ma jeden element multiset; na przykład `{{1, 2, 3}}`. Gdy multiset zawijania ma wiele elementów zestawów wielokrotnych (na przykład `{{1, 2}, {3, 4}}`), zagnieżdżone literały multiset — nie są obsługiwane.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora MULTISET do utworzenia wystąpienia zestawu wielokrotnego z listy wartości. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Zobacz także
- [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
