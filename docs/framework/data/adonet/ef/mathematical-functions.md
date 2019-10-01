---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 664d1a4f67ecced6713f83bf3dd11931c9b4dc18
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699998"
---
# <a name="mathematical-functions"></a>Funkcje matematyczne

.NET Framework Dostawca danych for SQL Server (SqlClient) oferuje funkcje matematyczne, które wykonują obliczenia na wartościach wejściowych, które są podawane jako argumenty, i zwracają wynik wartości liczbowej. Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje. W poniższej tabeli opisano funkcje matematyczne SqlClient.  
  
## <a name="absexpression"></a>ABS (wyrażenie)

Wykonuje funkcję wartość bezwzględną.

**Argumenty**

`expression`: `Int32`, `Int64`, `Double` lub `Decimal`.

**Wartość zwracana**

Wartość bezwzględna określonego wyrażenia.

**Przykład**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (wyrażenie)

Zwraca wartość arcus cosinus określonego wyrażenia.

**Argumenty**

`expression`: `Double`.

**Wartość zwracana**

@No__t-0.

**Przykład**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (wyrażenie)

Zwraca wartość arcus sinus określonego wyrażenia.

**Argumenty**

`expression`: `Double`.

**Wartość zwracana**

@No__t-0.

**Przykład**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN (wyrażenie)

Zwraca wartość arcus tangens określonego wyrażenia liczbowego.

**Argumenty**

`expression`: `Double`.

**Wartość zwracana**

@No__t-0.

**Przykład**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (wyrażenie, wyrażenie)

Zwraca kąt w radianach, którego tangens jest między dwoma określonymi wyrażeniami liczbowymi.

**Argumenty**

`expression`: `Double`.

**Wartość zwracana**

@No__t-0.

**Przykład**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>GÓRNy limit (wyrażenie)

Konwertuje określone wyrażenie na najmniejszą liczbę całkowitą, która jest większa lub równa.

**Argumenty**

`expression`: `Int32`, `Int64`, `Double` lub `Decimal`.

**Wartość zwracana**

@No__t-0, `Int64`, `Double` lub `Decimal`.

**Przykład** 

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS (wyrażenie)

Oblicza cosinus kąta określony kąt w radianach. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (wyrażenie)

Oblicza cotangens w postaci wartości kąta w radianach. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>STOPnie (radiany)

Zwraca odpowiedni kąt w stopniach. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double` lub `Decimal`. 

**Wartość zwracana** 

@No__t-0, `Int64`, `Double` lub `Decimal`. 

**Przykład** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (wyrażenie)

Oblicza wartość wykładniczą określonego wyrażenia liczbowego. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (wyrażenie)

Konwertuje określone wyrażenie na największą liczbę całkowitą mniejszą lub równą. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>Dziennik (wyrażenie)

Oblicza logarytm naturalny określonego wyrażenia `float`. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10 — (wyrażenie)

Zwraca logarytm dziesiętny określonego wyrażenia `Double`. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI ()

Zwraca wartość stałą liczby pi jako `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>Energia (numeric_expression, power_expression)

Oblicza wartość określonego wyrażenia do określonej potęgi.

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| @No__t-0, `Int64`, `Double` lub `Decimal`.|
|`power_expression`| @No__t-0 reprezentuje moc, do której należy podnieść `numeric_expression`.| 

**Wartość zwracana** 

Wartość określonego `numeric_expression` do określonego `power_expression`. 

**Przykład** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANy (wyrażenie)

Konwertuje stopnie na radiany. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double` lub `Decimal`. 

**Wartość zwracana** 

@No__t-0, `Int64`, `Double` lub `Decimal`. 

**Przykład** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND ([inicjator])

Zwraca losową wartość z przewartości od 0 do 1. 

**Argumenty** 

Wartość inicjatora jako `Int32`. Jeśli inicjator nie zostanie określony, aparat bazy danych SQL Server w losowo przypisze wartość inicjatora. W przypadku określonej wartości inicjatora zwrócony wynik jest zawsze taki sam.

**Wartość zwracana** 

Wartość losowa `Double` z przestawu od 0 do 1. 

**Przykład** 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (numeric_expression, Length [, funkcja])

Zwraca wyrażenie liczbowe zaokrąglone do określonej długości lub dokładności. 

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| @No__t-0, `Int64`, `Double` lub `Decimal`. 
|`length`| @No__t-0 reprezentuje precyzję, do której ma zostać zaokrąglony `numeric_expression`. Gdy `length` jest liczbą dodatnią, `numeric_expression` jest zaokrąglana do liczby miejsc dziesiętnych określonych przez `length`. Gdy `length` jest liczbą ujemną, `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, jak określono przez `length`.|
|`function` | Opcjonalny. @No__t-0 reprezentujący typ operacji do wykonania. Gdy funkcja jest pomijana lub ma wartość 0 (ustawienie domyślne), `numeric_expression` jest zaokrąglana. Gdy określona jest wartość inna niż 0, `numeric_expression` zostanie obcięta. |

**Wartość zwracana** 

Wartość określonego `numeric_expression` do określonego `power_expression`.

**Przykład** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN (wyrażenie) 

Zwraca wartość dodatnią (+ 1), zero (0) lub ujemną (-1) znak podanego wyrażenia. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double` lub `Decimal` 

**Wartość zwracana** 

@No__t-0, `Int64`, `Double` lub `Decimal`. 

**Przykład** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN (wyrażenie)

Oblicza sinus kątów o określonym kącie w radianach i zwraca wyrażenie `Double`. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT (wyrażenie)

Zwraca pierwiastek kwadratowy z podanego wyrażenia. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>KWADRAT (wyrażenie)

Zwraca kwadrat z podanego wyrażenia. 

**Argumenty** 

`expression`: `Double`. 

**Wartość zwracana** 

@No__t-0. 

**Przykład** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN (wyrażenie)

Oblicza tangens podanego wyrażenia.

**Argumenty** 

`expression`: `Double` 

**Wartość zwracana** 

`Double` 

**Przykład** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Zobacz także

- [Funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
