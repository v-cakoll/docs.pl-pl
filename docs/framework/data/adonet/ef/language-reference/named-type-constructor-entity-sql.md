---
title: Konstruktor typu nazwanego (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 26fb2839f0cc7d645f6ce6daea2d27e35868b63c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168795"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor typu nazwanego (jednostka SQL)
Używane do tworzenia wystąpień typów nominalna modelu koncepcyjnego, takich jak jednostki lub typy złożone.  
  
## <a name="syntax"></a>Składnia  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Argumenty  
 `identifier`  
 Wartość, która jest proste lub cytowanego identyfikatora. Aby uzyskać więcej informacji, zobacz [identyfikatorów](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Atrybuty typu, które są zakłada się, że w tej samej kolejności, w jakiej występują w deklaracji typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wystąpienia elementu o nazwie typy złożone i typy jednostek.  
  
## <a name="remarks"></a>Uwagi  
 W poniższych przykładach pokazano sposób tworzenia nominalna i złożone typy:  
  
 Poniższe wyrażenie tworzy wystąpienie `Person` typu:  
  
 `Person("abc", 12)`  
  
 Poniższe wyrażenie tworzenia wystąpienia tego typu złożonego:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Poniższe wyrażenie tworzy wystąpienie klasy zagnieżdżony typ złożony:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Poniższe wyrażenie tworzy wystąpienie jednostki z zagnieżdżony typ złożony:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego do wartości null:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa Konstruktor typu nazwanego w celu utworzenia wystąpienia typu modelu koncepcyjnego. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Zobacz także

- [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
