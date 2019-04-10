---
title: KLUCZ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 820d357baf8f3e17a10ced84babc6745512e572b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230034"
---
# <a name="key-entity-sql"></a>KLUCZ (jednostka SQL)
Wyodrębnia klucz referencyjnego lub wyrażenie jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 Klucz jednostki zawiera wartości klucza w odpowiedniej kolejności określonej jednostki lub odwołanie do jednostki. Ponieważ wiele zestawów jednostki mogą być oparte na ten sam typ, ten sam klucz może pojawić się w każdym zestawie jednostek. Aby odwołać unikatowy, należy użyć `REF`. Zwracany typ operatora klucza jest typem wiersza, który zawiera jedno pole dla każdego klucza podmiotu, w tej samej kolejności.  
  
 W poniższym przykładzie operator kluczy odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania. W tym przypadku rekordu typu przy użyciu dokładnie jedno pole odpowiadające `Id` właściwości.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora klucza do wyodrębnienia część klucza wyrażeniu zawierającym odwołania do typu. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
