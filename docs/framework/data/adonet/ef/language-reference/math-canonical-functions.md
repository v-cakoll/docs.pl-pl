---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250309"
---
# <a name="math-canonical-functions"></a>Funkcje matematyczne Canonical

Entity SQL obejmuje następujące funkcje matematyczne w postaci kanonicznej:
  
## <a name="absvalue"></a>ABS (wartość)

Zwraca wartość `value`bezwzględną.

**Argumenty**

`Int16` ,`Int32` ,,`Decimal`,, I. `Int64` `Byte` `Single` `Double`

**Wartość zwracana**

Typ `value`.

**Przykład**

`Abs(-2)`

## <a name="ceilingvalue"></a>Górny limit (wartość)

Zwraca najmniejszą liczbę całkowitą, która nie jest `value`mniejsza niż.

**Argumenty**

A `Single`, `Double`i .`Decimal`

**Wartość zwracana**

Typ `value`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Piętro (wartość)

Zwraca największą liczbę całkowitą, która nie jest większa `value`niż.

**Argumenty**

A `Single`, `Double`i .`Decimal`

**Wartość zwracana**

Typ `value`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Potęga (wartość, wykładnik)

Zwraca wynik określonego `value` do określonego `exponent`.

**Argumenty**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`Lub .`Decimal` |
|`exponent` | `Int64`, ,`Double`Lub .`Decimal` |

**Wartość zwracana**

Typ `value`.

**Przykład**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round (wartość)

Zwraca część całkowitą z `value`zaokrągloną do najbliższej liczby całkowitej.

**Argumenty**

A `Single`, `Double`i .`Decimal`

**Wartość zwracana**

Typ `value`.

**Przykład**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round (wartość, cyfry)

Zwraca zaokrąglony do najbliższego określonego `digits`. `value`

**Argumenty**

|  |  |
|--|--|
|`value`|`Double`lub `Decimal`.|
|`digits`|`Int16`lub `Int32`.|

**Wartość zwracana**

Typ `value`.

**Przykład**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>TRUNCATE (wartość, cyfry)

Zwraca wartość `value`, która jest obcinana do `digits`najbliższego określonego.

**Argumenty**

|  |  |
|--|--|
|`value`|`Double`lub `Decimal`.|
|`digits`|`Int16`lub `Int32`.|

**Wartość zwracana**

Typ `value`.

**Przykład**

`Truncate(748.58,1)`  
  
 Te funkcje zostaną zwrócone `null` , jeśli `null` dane wejściowe.  
  
 Równoważne funkcje są dostępne w dostawcy zarządzanym przez klienta programu Microsoft SQL. Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](canonical-functions.md)
