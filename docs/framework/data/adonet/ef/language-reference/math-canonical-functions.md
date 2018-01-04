---
title: Canonical funkcje matematyczne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1d8f959980be1c765a3eacba97992f42d9231201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="math-canonical-functions"></a>Canonical funkcje matematyczne
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obejmuje funkcje canonical matematyczne.  
  
 W poniższej tabeli przedstawiono obliczenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`Abs(` `value` `)`|Zwraca wartość bezwzględną liczby `value`.<br /><br /> **Argumenty**<br /><br /> `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, i `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|Zwraca największą liczbę całkowitą nie jest większa niż `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, i `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|Zwraca wynik określony `value` do określonego `exponent`.<br /><br /> **Argumenty**<br /><br /> `value`: `Int32, Int64, Double`, Lub `Decimal`.<br /><br /> `exponent`: `Int64``, Double`, Lub `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|Zwraca część całkowitą `value`, zaokrąglona do najbliższej liczby całkowitej.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, i `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|Zwraca `value`, zaokrąglona do najbliższej określony `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` lub `Decimal`.<br /><br /> `digits`: `Int16` lub `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|Zwraca `value`, został obcięty do najbliższej określony `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` lub `Decimal`.<br /><br /> `digits`: `Int16` lub `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Truncate(748.58,1)`|  
  
 Te funkcje będą zwracać `null` Jeśli podane `null` wejściowego.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [SqlClient Entity Framework funkcji](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
