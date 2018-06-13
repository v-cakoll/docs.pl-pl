---
title: SPŁASZCZANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 75463ed622ac969eb2690c4118861823479a2caa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760573"
---
# <a name="flatten-entity-sql"></a>SPŁASZCZANIE (jednostka SQL)
Konwertuje kolekcję spłaszczonych kolekcją kolekcji. Nowa kolekcja te same zawiera elementy, co stary kolekcji, ale bez struktury zagnieżdżone.  
  
## <a name="syntax"></a>Składnia  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Argumenty  
 `collection`  
 Dowolne prawidłowe wyrażenie zwracające kolekcją wartość kolekcji do spłaszczenia do jednej kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 `FLATTEN` jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa `FLATTEN` operator można przekonwertować na kolekcję spłaszczonych kolekcją kolekcji. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
