---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113744"
---
# <a name="mathematical-functions"></a>Funkcje matematyczne

.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje matematyczne, które wykonują obliczenia na wartości wejściowych, które są przekazywane jako argumenty i zwraca wynik wartość liczbową. Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje. W poniższej tabeli opisano funkcje matematyczne SqlClient.  
  
## <a name="absexpression"></a>ABS(Expression)

Wykonuje funkcję wartości bezwzględnej.

**Argumenty**

`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.

**Wartość zwracana**

Wartość bezwzględna z określonego wyrażenia.

**Przykład**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(Expression)

Zwraca arcus cosinus wartości podanego wyrażenia.

**Argumenty**

`expression`: ELEMENT `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(Expression)

Zwraca arcus sinus wartości podanego wyrażenia.

**Argumenty**

`expression`: ELEMENT `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(Expression)

Zwraca arcus tangens wartości podanego wyrażenia liczbowego.

**Argumenty**

`expression`: ELEMENT `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(Expression, Expression)

Zwraca kąt w radianach, którego tangens jest między dwoma określonych wyrażeń liczbowych.

**Argumenty**

`expression`: ELEMENT `Double`.

**Wartość zwracana**

A `Double`.

**Przykład**

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a>CEILING(Expression)

Konwertuje określony wyrażenie najmniejsza liczba całkowita, która jest większa niż lub równą jej.

**Argumenty**

`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.

**Wartość zwracana**

`Int32`, `Int64`, `Double`, Lub `Decimal`.

**Przykład** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(Expression)

Oblicza trygonometrycznych cosinus określonego kąta podany w radianach. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(Expression)

Oblicza trygonometrycznych cotangens kąta określonego w radianach. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>DEGREES(RADIANS)

Zwraca odpowiedni kąt w stopniach. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`. 

**Wartość zwracana** 

`Int32`, `Int64`, `Double`, Lub `Decimal`. 

**Przykład** 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(Expression)

Oblicza wartość wykładniczą określonego wyrażenia liczbowego. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** `SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR(Expression)

Konwertuje określony wyrażenie największą liczbą całkowitą mniejszą lub równą jej. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(Expression)

Oblicza logarytm naturalny z określonym `float` wyrażenia. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(Expression)

Zwraca logarytm o podstawie base 10 określonego `Double` wyrażenia. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Zwraca wartość stała pi jako `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a>ZASILANIA (numeric_expression, power_expression)

Oblicza wartość określone wyrażenie do określonej potęgi.

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, `Int64`, `Double`, Lub `Decimal`.|
|`power_expression`| A `Double` reprezentujący zasilania, do którego zostanie wywołane `numeric_expression`.| 

**Wartość zwracana** 

Wartość określonego `numeric_expression` określonej `power_expression`. 

**Przykład** 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIANS(Expression)

Konwertuje stopnie na radiany. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`. 

**Wartość zwracana** 

`Int32`, `Int64`, `Double`, Lub `Decimal`. 

**Przykład** 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([seed])

Zwraca wartość losową z zakresu od 0 do 1. 

**Argumenty** 

Wartość początkową jako `Int32`. Jeśli zalążek nie zostanie określony, aparatu bazy danych programu SQL Server w losowo wybranym momencie przypisuje wartość inicjatora. Wartości inicjatora określona zwracana jest zawsze taki sam.

**Wartość zwracana** 

Losowe `Double` wartość od 0 do 1. 

**Przykład** 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a>ROUND(Numeric_Expression, length[,Function])

Zwraca wartość wyrażenia liczbowego zaokrąglone do określonej długości lub dokładności. 

**Argumenty** 

|  |  |
|--|--|
|`numeric_expression`| `Int32`, `Int64`, `Double`, Lub `Decimal`. 
|`length`| `Int32` Reprezentujący dokładność, do którego `numeric_expression` ma zostać zaokrąglona. Gdy `length` jest liczbą dodatnią `numeric_expression` jest zaokrąglana do liczby miejsc dziesiętnych określonej przez `length`. Gdy `length` jest liczbą ujemną `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, określony przez `length`.|
|`function` | Opcjonalna. `Int32` Reprezentujący typ operacji do wykonania. Gdy funkcja zostanie pominięty lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana. Gdy wartość inną niż określono wartość 0, `numeric_expression` zostały obcięte. |

**Wartość zwracana** 

Wartość określonego `numeric_expression` określonej `power_expression`.

**Przykład** 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>SIGN(Expression) 

Zwraca wynik dodatni (+ 1), wartość zero (0) lub minus (-1) z określonego wyrażenia. 

**Argumenty** 

`expression`: `Int32`, `Int64`, `Double`, lub `Decimal` 

**Wartość zwracana** 

`Int32`, `Int64`, `Double`, Lub `Decimal`. 

**Przykład** 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(Expression)

Oblicza trygonometrycznych sinus określonego kąta podany w radianach, a następnie zwraca `Double` wyrażenia. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** `SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT(Expression)

Zwraca pierwiastek kwadratowy z określonego wyrażenia. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** `SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>SQUARE(Expression)

Zwraca kwadrat określone wyrażenie. 

**Argumenty** 

`expression`: ELEMENT `Double`. 

**Wartość zwracana** 

A `Double`. 

**Przykład** 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>Tan(Expression)

Oblicza tangens określonego wyrażenia.

**Argumenty** 

`expression`: `Double` 

**Wartość zwracana** 

`Double` 

**Przykład** 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Zobacz także

Aby uzyskać więcej informacji na temat funkcji matematycznych, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:  
  
**Program SQL Server 2005:** [funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))  
**Program SQL Server 2008:** [funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))  
**Program SQL Server 2012 lub nowszy:** [funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)   

 [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
