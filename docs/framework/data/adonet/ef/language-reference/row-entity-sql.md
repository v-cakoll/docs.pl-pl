---
title: WIERSZ (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d7b7e817330f4cd51eb163d437f17d6f546e721f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="row-entity-sql"></a>WIERSZ (jednostka SQL)
Tworzy rekordy anonimowe, strukturę typu z co najmniej jedną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca wartość do konstruowania typu wiersza.  
  
 `alias`  
 Określa aliasu dla wartości określonej w typu wiersza. Jeśli nie podano aliasu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias na podstawie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generowania reguł.  
  
## <a name="return-value"></a>Wartość zwracana  
 Typ wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Użyj konstruktorów wiersza w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do skonstruowania anonimowe, strukturę maszynowy rekordy z co najmniej jedną wartość. Typ wyniku konstruktorze wierszy jest typu wiersza, których typy pól odpowiadają typy wartości, które zostały użyte do konstruowania wiersza. Na przykład poniższe wyrażenie tworzy wartość typu `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Jeśli nie zostanie określona alias dla wyrażenia w Konstruktorze row, programu Entity Framework próbuje wygenerować. Aby uzyskać więcej informacji, zobacz sekcję "Zasady aliasowania" [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tematu.  
  
 Wyrażenie aliasów w Konstruktorze row mają zastosowanie następujące reguły:  
  
-   Wyrażenia w Konstruktorze row nie może odwoływać się do innych aliasów w tej samej konstruktora.  
  
-   Dwóch wyrażeń w tym samym Konstruktor row nie może mieć takiego samego aliasu.  
  
 Aby uzyskać więcej informacji o konstruktorów zapytania, zobacz [konstruowania typy](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki wykorzystuje operator wiersza do utworzenia anonimowe, strukturę typu rekordów. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Zobacz też  
 [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Definicje typu](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
