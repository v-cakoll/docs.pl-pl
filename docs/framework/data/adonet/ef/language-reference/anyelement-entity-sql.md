---
title: ANYELEMENT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 4dcbb80a9a850d193bfa88265a27a43c26869afe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196160"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (jednostka SQL)
Wyodrębnia element z kolekcji wielowartościowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję można wyodrębnić elementu z.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pojedynczy element w kolekcji lub dowolnego elementu, jeśli kolekcja zawiera więcej niż jedną; Jeśli kolekcja jest pusta, funkcja zwraca `null`. Jeśli `collection` jest kolekcją typów `Collection<T>`, następnie `ANYELEMENT(collection)` jest prawidłowym wyrażeniem, które zwracają wystąpienia typu `T`.  
  
## <a name="remarks"></a>Uwagi  
 ANYELEMENT wyodrębnia dowolnego elementu z kolekcji wielowartościowych. Na przykład, poniższy przykład próbuje wyodrębnić elementu pojedynczego wystąpienia z zestawu `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ANYELEMENT można wyodrębnić elementu z kolekcji wielowartościowych. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
