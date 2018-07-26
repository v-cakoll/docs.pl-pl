---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: c61db6d977614b95ea507b38c3890f2da8228158
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199305"
---
# <a name="math-canonical-functions"></a>Funkcje matematyczne Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obejmuje funkcje matematyczne canonical.  
  
 W poniższej tabeli przedstawiono obliczenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`Abs(value)`|Zwraca wartość bezwzględną liczby `value`.<br /><br /> **Argumenty**<br /><br /> `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Abs(-2)`|  
|`Ceiling(value)`|Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, i `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)] <br /><br /> [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(value)`|Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, i `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)] <br /><br /> [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(value, exponent)`|Zwraca wynik określony `value` określonej `exponent`.<br /><br /> **Argumenty**<br /><br /> `value`: `Int32, Int64, Double`, Lub `Decimal`.<br /><br /> `exponent`: `Int64`, `Double`, Lub `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Power(748.58,2)`|  
|`Round(value)`|Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.<br /><br /> **Argumenty**<br /><br /> A `Single`, `Double`, i `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Round(748.58)`|  
|`Round(value, digits)`|Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` lub `Decimal`.<br /><br /> `digits`: `Int16` lub `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Round(748.58,1)`|  
|`Truncate(value, digits)`|Zwraca `value`, obcięty do najbliższej wartości określone `digits`.<br /><br /> **Argumenty**<br /><br /> `value`: `Double` lub `Decimal`.<br /><br /> `digits`: `Int16` lub `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `value`.<br /><br /> **Przykład**<br /><br /> `Truncate(748.58,1)`|  
  
 Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
