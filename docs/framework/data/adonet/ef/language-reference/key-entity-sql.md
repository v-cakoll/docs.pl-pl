---
title: KLUCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 44ab5352c3b2a94cb210c3de775d2347d2df7fe7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250484"
---
# <a name="key-entity-sql"></a>KLUCZ (Entity SQL)
Wyodrębnia klucz odwołania lub wyrażenia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 Klucz jednostki zawiera wartości klucza w prawidłowej kolejności określonej jednostki lub odwołania do jednostki. Ponieważ wiele zestawów jednostek może opierać się na tym samym typie, ten sam klucz może pojawić się w każdym zestawie jednostek. Aby uzyskać unikatowe odwołanie, użyj `REF`. Zwracany typ operatora klucza jest typem wiersza, który zawiera jedno pole dla każdego klucza jednostki, w tej samej kolejności.  
  
 W poniższym przykładzie operator klucza jest przekazywać odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania. W tym przypadku typ rekordu z dokładnie jednym polem odpowiadającym `Id` właściwości.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora KEY do wyodrębnienia części klucza wyrażenia z odwołaniem do typu. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
