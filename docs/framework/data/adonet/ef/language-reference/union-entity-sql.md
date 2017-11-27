---
title: Unii (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b62d874a9885ed864282c765cf428f3c2a445745
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="union-entity-sql"></a>Unii (jednostka SQL)
Łączy wyniki dwóch lub więcej kwerend w jednej kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję do łączenia z kolekcji wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.  
  
 UNION  
 Określa, że wiele kolekcji są łączone i zwracane w postaci jednej kolekcji.  
  
 WSZYSTKIE  
 Określa, że wiele kolekcji są łączone i zwracane w postaci jednej kolekcji, w tym duplikaty. Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wynik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcji tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Unii jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora UNION ALL do łączenia wyniki dwa zapytania w jednej kolekcji. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
