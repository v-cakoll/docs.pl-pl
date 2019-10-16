---
title: KLUCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319701"
---
# <a name="key-entity-sql"></a>KLUCZ (Entity SQL)
Wyodrębnia klucz odwołania lub wyrażenia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 Klucz jednostki zawiera wartości klucza w prawidłowej kolejności określonej jednostki lub odwołania do jednostki. Ponieważ wiele zestawów jednostek może opierać się na tym samym typie, ten sam klucz może pojawić się w każdym zestawie jednostek. Aby uzyskać unikatowe odwołanie, użyj `REF`. Zwracany typ operatora klucza jest typem wiersza, który zawiera jedno pole dla każdego klucza jednostki, w tej samej kolejności.  
  
 W poniższym przykładzie operator klucza jest przekazywać odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania. W tym przypadku typ rekordu z dokładnie jednym polem odpowiadającym właściwości `Id`.  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora KEY do wyodrębnienia części klucza wyrażenia z odwołaniem do typu. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
