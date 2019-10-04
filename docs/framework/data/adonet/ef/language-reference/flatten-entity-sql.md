---
title: SPŁASZCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833808"
---
# <a name="flatten-entity-sql"></a>SPŁASZCZ (Entity SQL)
Konwertuje kolekcję kolekcji na spłaszczoną kolekcję. Nowa kolekcja zawiera wszystkie te same elementy co stara kolekcja, ale bez zagnieżdżonej struktury.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Argumenty  
 `collection`  
 Dowolne prawidłowe wyrażenie zwracające kolekcję kolekcji wartości do spłaszczenia do pojedynczej kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 `FLATTEN` to jeden z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej. Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla operatorów ustawionych [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora `FLATTEN` w celu przekonwertowania kolekcji kolekcji na spłaszczoną kolekcję. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
