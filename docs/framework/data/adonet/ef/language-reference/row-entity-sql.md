---
title: WIERSZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249252"
---
# <a name="row-entity-sql"></a>WIERSZ (Entity SQL)
Konstruuje anonimowe, strukturalnie wpisane rekordy z co najmniej jednej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca wartość do skonstruowania w typie wiersza.  
  
 `alias`  
 Określa alias dla wartości określonej w typie wiersza. Jeśli nie podano aliasu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] program podejmie próbę wygenerowania aliasu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] na podstawie reguł generowania aliasów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Typ wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktory wierszy w programie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] służą do konstruowania anonimowych, strukturalnie wpisanych rekordów z co najmniej jednej wartości. Typ wyniku konstruktora wierszy jest typem wiersza, którego typy pól odpowiadają typom wartości, które były używane do konstruowania wiersza. Na przykład następujące wyrażenie konstruuje wartość typu `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Jeśli nie podasz aliasu dla wyrażenia w konstruktorze wierszy, Entity Framework podejmie próbę wygenerowania jednego. Aby uzyskać więcej informacji, zobacz sekcję "reguły aliasów" tematu [identyfikatory](identifiers-entity-sql.md) .  
  
 W konstruktorze wierszy są stosowane następujące reguły:  
  
- Wyrażenia w konstruktorze wierszy nie mogą odwoływać się do innych aliasów w tym samym konstruktorze.  
  
- Dwa wyrażenia w tym samym konstruktorze wierszy nie mogą mieć tego samego aliasu.  
  
 Aby uzyskać więcej informacji na temat konstruktorów zapytań, zobacz [konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora wiersza do konstruowania anonimowych, strukturalnych rekordów z określonym typem. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Zobacz także

- [Konstruowanie typów](constructing-types-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Definicje typu](type-definitions-entity-sql.md)
