---
title: --(Komentarz) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 43b8cdbf5dbca8822645c27711f6984b8d741ea7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040286"
---
# <a name="---comment-entity-sql"></a>--(Komentarz) (Entity SQL)
zapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mogą zawierać komentarze. Dwie kreski (`--`) — Rozpoczynanie wiersza komentarza.  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Argumenty  
 `text_of_comment`  
 Jest ciągiem znaków, który zawiera tekst komentarza.  
  
## <a name="example"></a>Przykład  
 W poniższym zapytaniu Entity SQL pokazano, jak używać komentarzy. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
