---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149768"
---
# <a name="mathematical-functions"></a>Funkcje matematyczne

Dostawca danych programu .NET Framework dla programu SQL Server (SqlClient) udostępnia funkcje matematyczne, które wykonują obliczenia wartości wejściowych, które są dostarczane jako argumenty i zwracają wynik wartości liczbowej. Te funkcje znajdują się w obszarze nazw SqlServer, który jest dostępny podczas korzystania z SqlClient. Właściwość obszaru nazw dostawcy umożliwia entity framework, który prefiks jest używany przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje. W poniższej tabeli opisano funkcje matematyczne SqlClient.  
  
## <a name="absexpression"></a>ABS(wyrażenie)

Wykonuje funkcję wartości bezwzględnej.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .

**Wartość zwracana**

Wartość bezwzględna określonego wyrażenia.

**Przykład**

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a>ACOS(wyrażenie)

Zwraca wartość arccosine określonego wyrażenia.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a>ASIN(wyrażenie)

Zwraca wartość arcsine określonego wyrażenia.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a>ATAN(wyrażenie)

Zwraca wartość arctangent określonego wyrażenia liczbowego.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a>ATN2(wyrażenie, wyrażenie)

Zwraca kąt w radianach, którego styczna znajduje się między dwoma określonymi wyrażeniami liczbowymi.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a>CEILING(wyrażenie)

Konwertuje określone wyrażenie na najmniejszą liczę całkowitą, która jest większa lub równa.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .

**Wartość zwracana**

An `Int32` `Int64`, `Double`, `Decimal`, lub .

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a>COS(wyrażenie)

Oblicza cosine trygonometryczne określonego kąta w radianach.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.COS(45)`

## <a name="cotexpression"></a>COT(wyrażenie)

Oblicza tryb trygonometryczny określonego kąta w radianach.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a>STOPNIE(radiany)

Zwraca odpowiedni kąt w stopniach.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .

**Wartość zwracana**

An `Int32` `Int64`, `Double`, `Decimal`, lub .

**Przykład**

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a>EXP(wyrażenie)

Oblicza wykładniczą wartość określonego wyrażenia liczbowego.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**`SqlServer.EXP(1)`

## <a name="floorexpression"></a>FLOOR(wyrażenie)

Konwertuje określone wyrażenie na największą całkowitą mniejszą lub równą.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a>LOG(wyrażenie)

Oblicza logarytm naturalny określonego `float` wyrażenia.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.LOG(100)`

## <a name="log10expression"></a>LOG10(wyrażenie)

Zwraca logarytm base-10 określonego `Double` wyrażenia.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.LOG10(100)`

## <a name="pi"></a>PI()

Zwraca stałą wartość pi `Double`jako .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a>MOC (numeric_expression, power_expression)

Oblicza wartość określonego wyrażenia do określonej mocy.

**Argumenty**

|  |  |
|--|--|
|`numeric_expression`| An `Int32` `Int64`, `Double`, `Decimal`, lub .|
|`power_expression`| A, `Double` który reprezentuje moc, `numeric_expression`do której podnieść .|

**Wartość zwracana**

Wartość określona `numeric_expression` do określonego `power_expression`.

**Przykład**

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a>RADIAIANS(wyrażenie)

Konwertuje stopnie na radiany.

**Argumenty**

`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .

**Wartość zwracana**

An `Int32` `Int64`, `Double`, `Decimal`, lub .

**Przykład**

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a>RAND([materiał siewny])

Zwraca wartość losową od 0 do 1.

**Argumenty**

Wartość materiału siewnego jako wartość `Int32`. Jeśli materiał siewny nie jest określony, aparat bazy danych programu SQL Server przypisuje wartość źródłową losowo. Dla określonej wartości źródłowej zwracany wynik jest zawsze taki sam.

**Wartość zwracana**

Wartość `Double` losowa od 0 do 1.

**Przykład**

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a>ROUND(numeric_expression, długość[,funkcja])

Zwraca wyrażenie liczbowe, zaokrąglone do określonej długości lub precyzji.

**Argumenty**

|  |  |
|--|--|
|`numeric_expression`| An `Int32` `Int64`, `Double`, `Decimal`, lub .
|`length`| Który `Int32` reprezentuje dokładność, `numeric_expression` do której ma być zaokrąglona. Gdy `length` jest to `numeric_expression` liczba dodatnia, jest zaokrąglana `length`do liczby pozycji dziesiętnych określonych przez . Gdy `length` jest to `numeric_expression` liczba ujemna, jest zaokrąglana po `length`lewej stronie przecinka dziesiętnego, jak określono w programie .|
|`function` | Element opcjonalny. Który `Int32` reprezentuje typ operacji do wykonania. Gdy funkcja jest pominięta lub ma wartość `numeric_expression` 0 (domyślnie), jest zaokrąglana. Gdy określono wartość inną niż `numeric_expression` 0, jest obcinana. |

**Wartość zwracana**

Wartość określona `numeric_expression` do określonego `power_expression`.

**Przykład**

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a>ZNAK(wyrażenie)

Zwraca znak dodatni (+1), zero (0) lub ujemny (-1) określonego wyrażenia.

**Argumenty**

`expression`: `Int32` `Int64`, `Double`, , lub`Decimal`

**Wartość zwracana**

An `Int32` `Int64`, `Double`, `Decimal`, lub .

**Przykład**

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a>SIN(wyrażenie)

Oblicza sinus trygonometryczny określonego kąta w radianach i zwraca `Double` wyrażenie.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**`SqlServer.SIN(20)`

## <a name="sqrtexpression"></a>SQRT(wyrażenie)

Zwraca pierwiastek kwadratowy określonego wyrażenia.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**`SqlServer.SQRT(3600)`

## <a name="squareexpression"></a>KWADRAT(wyrażenie)

Zwraca kwadrat określonego wyrażenia.

**Argumenty**

`expression`: `Double`A .

**Wartość zwracana**

Klasa `Double`.

**Przykład**

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a>TAN(wyrażenie)

Oblicza styczną określonego wyrażenia.

**Argumenty**

`expression`: `Double`

**Wartość zwracana**

`Double`

**Przykład**

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a>Zobacz też

- [Funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
