---
title: WIERSZ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 676080a6cc4208ea1a4d72b85a4a55e01fafe638
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641445"
---
# <a name="row-entity-sql"></a>WIERSZ (jednostka SQL)
Tworzy rekordy anonimowe, strukturalnie wpisane z co najmniej jedną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca wartość do konstruowania typu wiersza.  
  
 `alias`  
 Określa alias dla wartości określonej w typu wiersza. Jeśli nie zostanie podany alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje wygenerować na podstawie alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] reguły generowania aliasu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Typ wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Użyj wiersza konstruktorów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konstruowania anonimowe, strukturalnie wpisane rekordy z co najmniej jedną wartość. Typ wyniku w Konstruktorze wierszy jest typu wiersza, w których typy pól odpowiadają typy wartości, które zostały użyte do konstruowania wiersza. Na przykład poniższe wyrażenie tworzy wartość typu `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Jeśli nie podasz alias wyrażenia w Konstruktorze wierszy, platformy Entity Framework podejmie próbę go wygeneruje. Aby uzyskać więcej informacji, zobacz sekcję "Zasady aliasowania" [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tematu.  
  
 Następujące reguły stosuje się do wyrażenia aliasów w Konstruktorze wierszy:  
  
- Wyrażenia w Konstruktorze row nie może odwoływać się do innych aliasów w tej samej konstruktora.  
  
- Dwóch wyrażeń w tym samym Konstruktor row nie może mieć takiego samego aliasu.  
  
 Aby uzyskać więcej informacji o konstruktory zapytania, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora wiersz do konstruowania anonimowe, strukturalnie kontrolą typów rekordów. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Zobacz także

- [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Definicje typu](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
