---
title: "SPŁASZCZANIE (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 44abbcf90ec2607824d75ce89284c356e6096af2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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
 `FLATTEN`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa `FLATTEN` operator można przekonwertować na kolekcję spłaszczonych kolekcją kolekcji. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
