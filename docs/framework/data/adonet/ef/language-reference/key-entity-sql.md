---
title: KLUCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150172"
---
# <a name="key-entity-sql"></a>KLUCZ (Entity SQL)
Wyodrębnia klucz odwołania lub wyrażenia jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 Klucz jednostki zawiera wartości klucza w prawidłowej kolejności określonego odwołania do encji lub jednostki. Ponieważ wiele zestawów jednostek może być opartych na tym samym typie, ten sam klucz może pojawić się w każdym zestawie jednostek. Aby uzyskać unikatowe `REF`odwołanie, użyj programu . Typ zwracany operatora KEY jest typem wiersza, który zawiera jedno pole dla każdego klucza encji w tej samej kolejności.  
  
 W poniższym przykładzie operator klucza jest przekazywana odwołanie do BadOrder jednostki i zwraca kluczową część tego odwołania. W takim przypadku typ rekordu z dokładnie jednym `Id` polem odpowiadającym właściwości.  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa key operatora wyodrębnić kluczową część wyrażenia z odwołania typu. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [Ref](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
