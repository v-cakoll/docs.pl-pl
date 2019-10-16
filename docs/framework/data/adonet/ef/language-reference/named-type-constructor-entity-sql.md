---
title: Konstruktor nazwanego typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f40adce1a9e031ed0b7cd5d03d9c63db255aa610
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319572"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor nazwanego typu (Entity SQL)
Służy do tworzenia wystąpień typów nominalnych modelu koncepcyjnego, takich jak jednostki lub typy złożone.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Argumenty  
 `identifier`  
 Wartość, która jest prostym lub w cudzysłowie identyfikatorem. Aby uzyskać więcej informacji, zobacz [identyfikatory](identifiers-entity-sql.md)  
  
 `expression`  
 Atrybuty typu, które mają być w tej samej kolejności, w jakiej występują w deklaracji typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wystąpienia o nazwanych typach złożonych i typach jednostek.  
  
## <a name="remarks"></a>Uwagi  
 W poniższych przykładach pokazano, jak utworzyć typy nominalne i złożone:  
  
 Poniższe wyrażenie tworzy wystąpienie typu `Person`:  
  
 `Person("abc", 12)`  
  
 Poniższe wyrażenie tworzy wystąpienie typu złożonego:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Poniższe wyrażenie tworzy wystąpienie zagnieżdżonego typu złożonego:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Poniższe wyrażenie tworzy wystąpienie jednostki z zagnieżdżonym typem złożonym:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego na null: `MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa konstruktora nazwanego typu w celu utworzenia wystąpienia typu modelu koncepcyjnego. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a>Zobacz także

- [Konstruowanie typów](constructing-types-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
