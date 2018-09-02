---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442788"
---
# <a name="math-canonical-functions"></a>Funkcje matematyczne Canonical

Jednostka SQL obejmuje następujące funkcje matematyczne canonical:
  
## <a name="absvalue"></a>ABS(Value)

Zwraca wartość bezwzględną liczby `value`.

**Argumenty**

`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.

**Wartość zwracana**

Typ `value`.

**Przykład**

`Abs(-2)`

## <a name="ceilingvalue"></a>CEILING(Value)

Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.

**Argumenty**

A `Single`, `Double`, i `Decimal`.

**Wartość zwracana**

Typ `value`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>FLOOR(Value)

Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.

**Argumenty**

A `Single`, `Double`, i `Decimal`.

**Wartość zwracana**

Typ `value`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Zasilania (wartość wykładnika)

Zwraca wynik określony `value` określonej `exponent`.

**Argumenty**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`, Lub `Decimal`. |
|`exponent` | `Int64`, `Double`, Lub `Decimal`. |

**Wartość zwracana**

Typ `value`.

**Przykład**

`Power(748.58,2)`

## <a name="roundvalue"></a>ROUND(Value)

Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.

**Argumenty**

A `Single`, `Double`, i `Decimal`.

**Wartość zwracana**

Typ `value`.

**Przykład**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Zaokrąglij (wartość cyfr)

Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.

**Argumenty**

|  |  |
|--|--|
|`value`|`Double` lub `Decimal`.|
|`digits`|`Int16` lub `Int32`.|

**Wartość zwracana**

Typ `value`.

**Przykład**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Obetnij (wartość cyfr)

Zwraca `value`, obcięty do najbliższej wartości określone `digits`.

**Argumenty**

|  |  |
|--|--|
|`value`|`Double` lub `Decimal`.|
|`digits`|`Int16` lub `Int32`.|

**Wartość zwracana**

Typ `value`.

**Przykład**

`Truncate(748.58,1)`  
  
 Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
