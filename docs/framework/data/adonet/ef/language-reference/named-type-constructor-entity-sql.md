---
title: Konstruktor nazwanego typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c7027614e5667acedb02d871a09df1ac9d799405
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250006"
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor nazwanego typu (Entity SQL)
Służy do tworzenia wystąpień typów nominalnych modelu koncepcyjnego, takich jak jednostki lub typy złożone.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Poniższe wyrażenie tworzy wystąpienie `Person` typu:  
  
 `Person("abc", 12)`  
  
 Poniższe wyrażenie tworzy wystąpienie typu złożonego:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Poniższe wyrażenie tworzy wystąpienie zagnieżdżonego typu złożonego:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Poniższe wyrażenie tworzy wystąpienie jednostki z zagnieżdżonym typem złożonym:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego do wartości null:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa konstruktora nazwanego typu w celu utworzenia wystąpienia typu modelu koncepcyjnego. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Zobacz także

- [Konstruowanie typów](constructing-types-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
