---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182484"
---
# <a name="mathematical-functions"></a>Funkcje matematyczne

.NET Framework Dostawca danych for SQL Server (SqlClient) oferuje funkcje matematyczne, które wykonują obliczenia na wartościach wejściowych, które są podawane jako argumenty, i zwracają wynik wartości liczbowej. Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje. W poniższej tabeli opisano funkcje matematyczne SqlClient.  
  
## <a name="absexpression"></a>ABS (wyrażenie)

Wykonuje funkcję wartość bezwzględną.

**Argumenty**

`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64`

**Wartość zwracana**

Wartość bezwzględna określonego wyrażenia.

**Przykład**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS (wyrażenie)

Zwraca wartość arcus cosinus określonego wyrażenia.

**Argumenty**

`expression`: A `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN (wyrażenie)

Zwraca wartość arcus sinus określonego wyrażenia.

**Argumenty**

`expression`: A `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN (wyrażenie)

Zwraca wartość arcus tangens określonego wyrażenia liczbowego.

**Argumenty**

`expression`: A `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2 (wyrażenie, wyrażenie)

Zwraca kąt w radianach, którego tangens jest między dwoma określonymi wyrażeniami liczbowymi.

**Argumenty**

`expression`: A `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>GÓRNy limit (wyrażenie)

Konwertuje określone wyrażenie na najmniejszą liczbę całkowitą, która jest większa lub równa.

**Argumenty**

`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64`

**Wartość zwracana**

`Int32`, ,,`Double`Lub .`Decimal` `Int64`

**Przykład** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS (wyrażenie)

Oblicza cosinus kąta określony kąt w radianach. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT (wyrażenie)

Oblicza cotangens w postaci wartości kąta w radianach. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>STOPnie (radiany)

Zwraca odpowiedni kąt w stopniach. 

**Argumenty** 

`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64` 

**Wartość zwracana** 

`Int32`, ,,`Double`Lub .`Decimal` `Int64` 

**Przykład** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP (wyrażenie)

Oblicza wartość wykładniczą określonego wyrażenia liczbowego. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR (wyrażenie)

Konwertuje określone wyrażenie na największą liczbę całkowitą mniejszą lub równą. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>Dziennik (wyrażenie)

Oblicza logarytm naturalny określonego `float` wyrażenia. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10 — (wyrażenie)

Zwraca logarytm dziesiętny dla podanego `Double` wyrażenia. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Zwraca wartość stałą liczby pi jako `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>Energia (numeric_expression, power_expression)

Oblicza wartość określonego wyrażenia do określonej potęgi.

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, ,,`Double`Lub .`Decimal` `Int64`|
|`power_expression`| Reprezentuje moc, do której należy `numeric_expression`podnieść. `Double`| 

**Wartość zwracana** 

Wartość określonego `numeric_expression` `power_expression`elementu. 

**Przykład** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANy (wyrażenie)

Konwertuje stopnie na radiany. 

**Argumenty** 

`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64` 

**Wartość zwracana** 

`Int32`, ,,`Double`Lub .`Decimal` `Int64` 

**Przykład** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND ([inicjator])

Zwraca losową wartość z przewartości od 0 do 1. 

**Argumenty** 

Wartość inicjatora jako `Int32`. Jeśli inicjator nie zostanie określony, aparat bazy danych SQL Server w losowo przypisze wartość inicjatora. W przypadku określonej wartości inicjatora zwrócony wynik jest zawsze taki sam.

**Wartość zwracana** 

Wartość losowa `Double` od 0 do 1. 

**Przykład** 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND (numeric_expression, Length [, funkcja])

Zwraca wyrażenie liczbowe zaokrąglone do określonej długości lub dokładności. 

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, ,,`Double`Lub .`Decimal` `Int64` 
|`length`| Reprezentuje precyzję, do której `numeric_expression` ma zostać zaokrąglona wartość. `Int32` Gdy `length` jest liczbą dodatnią, `numeric_expression` jest zaokrąglana do liczby pozycji dziesiętnych określonych przez `length`. Gdy `length` jest liczbą ujemną, `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, zgodnie z opisem w `length`.|
|`function` | Opcjonalny. `Int32` Reprezentuje typ operacji do wykonania. Gdy funkcja jest pomijana lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana. Gdy określona jest wartość inna niż 0, `numeric_expression` zostanie obcięta. |

**Wartość zwracana** 

Wartość określonego `numeric_expression` `power_expression`elementu.

**Przykład** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN (wyrażenie) 

Zwraca wartość dodatnią (+ 1), zero (0) lub ujemną (-1) znak podanego wyrażenia. 

**Argumenty** 

`expression`: `Int32`, `Int64`, lub`Double``Decimal` 

**Wartość zwracana** 

`Int32`, ,,`Double`Lub .`Decimal` `Int64` 

**Przykład** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN (wyrażenie)

Oblicza sinus kątów o określonym kącie w radianach i zwraca `Double` wyrażenie. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT (wyrażenie)

Zwraca pierwiastek kwadratowy z podanego wyrażenia. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>KWADRAT (wyrażenie)

Zwraca kwadrat z podanego wyrażenia. 

**Argumenty** 

`expression`: A `Double`. 

**Wartość zwracana** 

A `Double`. 

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

Aby uzyskać więcej informacji na temat funkcji matematycznych obsługiwanych przez program SqlClient, zapoznaj się z dokumentacją dla SQL Server wersji określonej w manifeście dostawcy SqlClient:

- **SQL Server 2005:** [Funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))
- **SQL Server 2008:** [Funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))
- **SQL Server 2012 i nowsze:** [Funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)

- [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
