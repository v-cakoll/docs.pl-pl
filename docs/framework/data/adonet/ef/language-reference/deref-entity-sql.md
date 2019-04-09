---
title: DEREF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 57f7c61d8e4de2a63708ef6d4437ca53de854af9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116873"
---
# <a name="deref-entity-sql"></a>DEREF (jednostka SQL)
Wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość jednostki, do którego istnieje odwołanie.  
  
## <a name="remarks"></a>Uwagi  
 DEREF operator wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu. Na przykład jeśli `r` jest odwołanie do typu ref\<T >, `Deref(r)` to wyrażenie typu `T` , daje jednostek odwołuje się `r`. Jeśli wartość odwołania ma wartość null lub jest delegujące (czyli docelowego odwołania nie istnieje), wynik operatora DEREF ma wartość null.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora DEREF próbę wartością odniesienia i wygenerować wyłuskania wynik tego obiektu. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do metody ExecutePrimitiveTypeQuery:  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
