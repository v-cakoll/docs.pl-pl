---
title: --(Komentarz) (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: c10b17931c6024e2a9e947083747435d8aa54fa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339518"
---
# <a name="---comment-entity-sql"></a>--(Komentarz) (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania mogą zawierać komentarzy. Dwa łączniki (`--`) uruchom wiersz komentarza.  
  
## <a name="syntax"></a>Składnia  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Argumenty  
 `text_of_comment`  
 Jest ciąg znaków, który zawiera tekst komentarza.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki pokazuje, jak używać komentarzy. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
