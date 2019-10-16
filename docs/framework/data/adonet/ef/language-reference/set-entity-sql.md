---
title: Ustaw (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 9d4cdeac317509fd61741a19276a6764a1c2bfce
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319354"
---
# <a name="set-entity-sql"></a>Ustaw (Entity SQL)
Wyrażenie SET służy do konwertowania kolekcji obiektów do zestawu przez wypróbowanie nowej kolekcji z usuniętymi wszystkimi zduplikowanymi elementami.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie Set `SET(c)` jest logicznym odpowiednikiem następującej instrukcji SELECT:  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` to jeden z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej. Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla operatorów ustawionych [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa wyrażenia zestawu do konwertowania kolekcji obiektów na zestaw. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
