---
title: Konstruktor typu nazwanego (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b572d09b812d43fa64e30a3058da9af01d29b747
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="named-type-constructor-entity-sql"></a>Konstruktor typu nazwanego (jednostka SQL)
Używany do tworzenia wystąpień typów nominalnego modelu koncepcyjnego, takich jak jednostki lub typów złożonych.  
  
## <a name="syntax"></a>Składnia  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Argumenty  
 `identifier`  
 Wartość, która jest identyfikatorem prostej lub ujętego w cudzysłów. Aby uzyskać więcej informacji, zobacz [identyfikatorów](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Atrybuty typu, które są rozpatrywane w tej samej kolejności występującym w deklaracji typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wystąpienia nazwane typy złożone i typy jednostek.  
  
## <a name="remarks"></a>Uwagi  
 W poniższych przykładach pokazano, jak utworzyć nominalnego i złożone typy:  
  
 Poniższe wyrażenie tworzy wystąpienie `Person` typu:  
  
 `Person("abc", 12)`  
  
 Poniższe wyrażenie powoduje utworzenie wystąpienia typu złożonego:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Poniższe wyrażenie tworzy wystąpienie typu złożonego zagnieżdżone:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Poniższe wyrażenie tworzy wystąpienie obiektu z zagnieżdżony typ złożony:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego do wartości null:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa konstruktora typu o nazwie do utworzenia wystąpienia typu modelu koncepcyjnego. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Zobacz też  
 [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
