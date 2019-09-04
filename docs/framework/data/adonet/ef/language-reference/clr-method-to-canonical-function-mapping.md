---
title: Metody mapowania funkcji Canonical CLR
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 6f14ad8d9e8f919fe820447cc991b102319b38d5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251222"
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metody mapowania funkcji Canonical CLR

Entity Framework zawiera zestaw funkcji kanonicznych, które implementują funkcje, które są wspólne dla wielu systemów baz danych, takich jak manipulowanie ciągami i funkcje matematyczne. Dzięki temu deweloperzy mogą kierować do szerokiego zakresu systemów baz danych. Po wywołaniu z technologii zapytań, takiej jak LINQ to Entities, te funkcje kanoniczne są tłumaczone na poprawną odpowiednią funkcję magazynu dla używanego dostawcy. Dzięki temu wywołania funkcji są wyrażane w typowym formacie między źródłami danych, co zapewnia spójne środowisko zapytań w ramach źródeł danych. Operatory bitowe and, OR, NOT i XOR są również mapowane na funkcje kanoniczne, gdy argument operacji jest typu liczbowego. W przypadku operandów logicznych operatory bitowe and, OR, NOT i XOR obliczają operacje logiczne i, OR, NOT i XOR argumentów operacji. Aby uzyskać więcej informacji, zobacz [funkcje kanoniczne](canonical-functions.md).

W przypadku scenariuszy LINQ zapytania dotyczące Entity Framework polegają na mapowaniu określonych metod CLR na metody z bazowego źródła danych za pomocą funkcji kanonicznych. Wszelkie wywołania metod w zapytaniu LINQ to Entities, które nie są jawnie zamapowane na funkcję kanoniczną, spowodują wyrzucanie wyjątku czasu wykonywania <xref:System.NotSupportedException> .

## <a name="systemstring-method-static-mapping"></a>Mapowanie metody System. String (static)

|System. String — Metoda (statyczna)|Funkcja kanoniczna|
|-------------------------------------|------------------------|
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat(Concat(`str0`, `str1`), `str2`)|
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat(Concat(Concat(`str0`, `str1`), `str2`), `str3`)|
|Wartość logiczna Equals ( `a`String, `b`String)|= — Operator|
|Wartość logiczna IsNullOrEmpty ( `value`ciąg)|(IsNull (`value`)) lub length (`value`) = 0|
|Wartość logiczna op_Equality ( `a`String, `b`String)|= — Operator|
|Wartość logiczna op_Inequality ( `a` String, `b`String)|!= - Operator|
|Microsoft.VisualBasic.Strings.Trim(String `str`)|Trim(`str`)|
|Microsoft.VisualBasic.Strings.LTrim(String `str`)|Ltrim(`str`)|
|Microsoft.VisualBasic.Strings.RTrim(String `str`)|Rtrim(`str`)|
|Microsoft.VisualBasic.Strings.Len(String `expression`)|Długość (`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Po lewej`str`( `Length`,)|
|Microsoft. VisualBasic. Strings. Mid (String `str`, Int32 `Start`, Int32 `Length`)|Podciąg (`str`, `Start`, `Length`)|
|Microsoft.VisualBasic.Strings.Right(String `str`, Int32 `Length`)|Right (`str`, `Length`)|
|Microsoft.VisualBasic.Strings.UCase(String `Value`)|ToUpper (`Value`)|
|Microsoft. VisualBasic. Strings. LCase (wartość ciągu)|ToLower (`Value`)|

## <a name="systemstring-method-instance-mapping"></a>Mapowanie metody System. String (wystąpienie)

|System. String — Metoda (wystąpienie)|Funkcja kanoniczna|Uwagi|
|---------------------------------------|------------------------|-----------|
|Wartość logiczna zawiera ( `value`ciąg)|`this`JAK "%`value`%"|Jeśli `value` nie jest stałą, to mapuje do IndexOf (`this`, `value`) > 0|
|Wartość logiczna EndsWith ( `value`ciąg)|`this` LIKE `'`%`value`'|Jeśli `value` nie jest stałą, to mapuje na prawo (`this`, Długość (`value`)) = `value`.|
|Wartość logiczna StartsWith ( `value`ciąg)|`this`LIKE "`value`%"|Jeśli `value` nie jest stałą, to mapuje do IndexOf (`this`, `value`) = 1.|
|Długość|Długość (`this`)||
|Int32 IndexOf (ciąg `value`)|IndexOf (`this`, `value`)-1||
|Insert system. String (Int32 `startIndex`, String `value`)|`this`Concat (concat (, 1, `startIndex`), `value`), podciąg (`this`, `startIndex`+ 1, Długość (`this`)- `startIndex`))||
|Usuwanie z System. String ( `startIndex`Int32)|Podciąg (`this`, 1, `startIndex`)||
|Usuwanie z System. String ( `startIndex`Int32, `count`Int32)|`this`Concat (, 1,`count``startIndex``this` + ), podciąg (  +  `this` `startIndex`, `startIndex` `count` + 1, Długość ()-()))|Polecenie Remove`startIndex`( `count`,) jest obsługiwane tylko `count` wtedy, gdy jest liczbą całkowitą większą lub równą 0.|
|Zastąp system. String ( `oldValue`ciąg, `newValue`ciąg)|Zamień (`this`, `oldValue`, `newValue`)||
|Reciąg system. String (Int32 `startIndex`)|Podciąg (`this`, `startIndex` + 1, Długość (`this`) — `startIndex`)||
|Podciąg system. String (Int32 `startIndex`, Int32 `length`)|Podciąg (`this`, `startIndex` + 1, `length`)||
|System. String ToLower ()|ToLower (`this`)||
|System. String ToUpper ()|ToUpper (`this`)||
|Trim system. String ()|Trim(`this`)||
|System. String TrimEnd (Char [] `trimChars`)|RTrim(`this`)||
|System. String TrimStart (Char []`trimChars`)|LTrim(`this`)||
|Wartość logiczna jest równa (ciąg `value`)|= — Operator||

## <a name="systemdatetime-method-static-mapping"></a>Mapowanie metody System. DateTime (static)

|System. DateTime — Metoda (statyczna)|Funkcja kanoniczna|Uwagi|
|---------------------------------------|------------------------|-----------|
|Wartość logiczna Equals ( `t1`DateTime, `t2`DateTime)|= — Operator||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Wartość logiczna op_Equality ( `d1`DateTime, `d2`DateTime)|= — Operator||
|Wartość logiczna op_GreaterThan ( `t1`DateTime, `t2`DateTime)|operator >||
|Wartość logiczna op_GreaterThanOrEqual ( `t1`DateTime, `t2`DateTime)|> = — operator||
|Wartość logiczna op_Inequality ( `t1`DateTime, `t2`DateTime)|!= - Operator||
|Wartość logiczna op_LessThan ( `t1`DateTime, `t2`DateTime)|operator <||
|Wartość logiczna op_LessThanOrEqual ( `t1`DateTime, `t2`DateTime)|< = — operator||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval` jako DateInterval,\_<br /><br /> ByVal `DateValue` jako DateTime,\_<br /><br /> Opcjonalna `FirstDayOfWeekValue` opcja ByVal jako pierwszydzieńtygodnia = VbSunday,\_<br /><br /> Opcjonalne ByVal `FirstWeekOfYearValue` as FirstWeekOfYear = VbFirstJan1\_<br /><br /> ) Jako liczba całkowita||Aby uzyskać więcej informacji, zobacz sekcję funkcji DatePart.|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year ()||
|Microsoft.VisualBasic.DateAndTime.Month(DateTime `TimeValue`)|Miesiąc ()||
|Microsoft. VisualBasic. DateAndTime. Day (DateTime `TimeValue`)|Day()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minuta ()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Sekunda ()||

## <a name="systemdatetime-method-instance-mapping"></a>Mapowanie metody System. DateTime (Instance)

|System. DateTime (wystąpienie)|Funkcja kanoniczna|
|-----------------------------------------|------------------------|
|Wartość logiczna Equals ( `value`DateTime)|= — Operator|
|Dzień|Dzień (`this`)|
|Godzina|Godzina (`this`)|
|Milisekund|Millisecond(`this`)|
|Minuta|Minuta`this`()|
|Bieżącym|Miesiąc (`this`)|
|Sekunda|Sekunda`this`()|
|Rok|Year (`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>Mapowanie metody System. DateTimeOffset (wystąpienie)

Mapowanie pokazane dla `get` metod na liście właściwości.

|System. DateTimeOffset — Metoda (wystąpienie)|Funkcja kanoniczna|Uwagi|
|-----------------------------------------------|------------------------|-----------|
|Dzień|Dzień (`this`)|Nieobsługiwane w przypadku SQL Server 2005.|
|Godzina|Godzina (`this`)|Nieobsługiwane w przypadku SQL Server 2005.|
|Milisekund|Millisecond(`this`)|Nieobsługiwane w przypadku SQL Server 2005.|
|Minuta|Minuta`this`()|Nieobsługiwane w przypadku SQL Server 2005.|
|Bieżącym|Miesiąc (`this`)|Nieobsługiwane w przypadku SQL Server 2005.|
|Sekunda|Sekunda`this`()|Nieobsługiwane w przypadku SQL Server 2005.|
|Rok|Year (`this`)|Nieobsługiwane w przypadku SQL Server 2005.|

> [!NOTE]
> Metoda zwraca `true` czy porównywane <xref:System.DateTimeOffset> obiekty są równe; <xref:System.DateTimeOffset.Equals%2A> `false` w przeciwnym razie. Metoda zwraca wartość 0, 1 lub-1, w zależności od tego, czy <xref:System.DateTimeOffset> porównany obiekt jest równy, większy lub mniejszy niż odpowiednio. <xref:System.DateTimeOffset.CompareTo%2A>

## <a name="systemdatetimeoffset-method-static-mapping"></a>Mapowanie metody System. DateTimeOffset (static)

Mapowanie pokazane dla `get` metod na liście właściwości.

|System. DateTimeOffset — Metoda (statyczna)|Funkcja kanoniczna|Uwagi|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Nieobsługiwane w przypadku SQL Server 2005.|

## <a name="systemtimespan-method-instance-mapping"></a>Mapowanie metody System. TimeSpan (wystąpienie)

Mapowanie pokazane dla `get` metod na liście właściwości.

|System. TimeSpan — Metoda (wystąpienie)|Funkcja kanoniczna|Uwagi|
|-----------------------------------------|------------------------|-----------|
|Liczb|Godzina (`this`)|Nieobsługiwane w przypadku SQL Server 2005.|
|MS|Millisecond(`this`)|Nieobsługiwane w przypadku SQL Server 2005.|
|Minuty|Minuta`this`()|Nieobsługiwane w przypadku SQL Server 2005.|
|S|Sekunda`this`()|Nieobsługiwane w przypadku SQL Server 2005.|

> [!NOTE]
> Metoda zwraca `true` czy porównywane <xref:System.TimeSpan> obiekty są równe; <xref:System.TimeSpan.Equals%2A> `false` w przeciwnym razie. Metoda zwraca wartość 0, 1 lub-1, w zależności od tego, czy <xref:System.TimeSpan> porównany obiekt jest równy, większy lub mniejszy niż odpowiednio. <xref:System.TimeSpan.CompareTo%2A>

### <a name="datepart-function"></a>DatePart — funkcja

Funkcja jest mapowana na jedną z kilku różnych funkcji kanonicznych, w zależności od `Interval`wartości. `DatePart` W poniższej tabeli przedstawiono mapowanie funkcji kanonicznej dla obsługiwanych wartości `Interval`:

|Wartość interwału|Funkcja kanoniczna|
|--------------------|------------------------|
|DateInterval.Year|Year ()|
|DateInterval.Month|Miesiąc ()|
|DateInterval.Day|Day()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|Minuta ()|
|DateInterval.Second|Sekunda ()|

## <a name="mathematical-function-mapping"></a>Mapowanie funkcji matematycznych

|CLR — Metoda|Funkcja kanoniczna|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|Górny`d`limit ()|
|System.Decimal.Floor(Decimal `d`)|Podłoga`d`()|
|System.Decimal.Round(Decimal `d`)|Round (`d`)|
|System.Math.Ceiling(Decimal `d`)|Górny`d`limit ()|
|System.Math.Floor(Decimal `d`)|Podłoga`d`()|
|System. Math. Round (Decimal `d`)|Round (`d`)|
|System.Math.Ceiling(Double `a`)|Górny`a`limit ()|
|System.Math.Floor(Double `a`)|Podłoga`a`()|
|System. Math. Round (Double `a`)|Round (`a`)|
|System.Math.Round(Double value, Int16 digits)|Round (wartość, cyfry)|
|System.Math.Round(Double value, Int32 digits)|Round (wartość, cyfry)|
|System.Math.Round(Decimal value, Int16 digits)|Round (wartość, cyfry)|
|System.Math.Round(Decimal value, Int32, digits)|Round (wartość, cyfry)|
|System.Math.Abs(Int16 value)|ABS (wartość)|
|System.Math.Abs(Int32 value)|ABS (wartość)|
|System.Math.Abs(Int64 value)|ABS (wartość)|
|System.Math.Abs(Byte value)|ABS (wartość)|
|System.Math.Abs(Single value)|ABS (wartość)|
|System.Math.Abs(Double value)|ABS (wartość)|
|System.Math.Abs(Decimal value)|ABS (wartość)|
|System.Math.Truncate(Double value, Int16 digits)|TRUNCATE (wartość, cyfry)|
|System.Math.Truncate(Double value, Int32 digits)|TRUNCATE (wartość, cyfry)|
|System.Math.Truncate(Decimal value, Int16 digits)|TRUNCATE (wartość, cyfry)|
|System.Math.Truncate(Decimal value, Int32 digits)|TRUNCATE (wartość, cyfry)|
|System.Math.Power(Int32 value, Int64 exponent)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość Int32, podwójny wykładnik)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość Int32, wykładnik dziesiętny)|Potęga (wartość, wykładnik)|
|System.Math.Power(Int64 value, Int64 exponent)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość Int64, podwójny wykładnik)|Potęga (wartość, wykładnik)|
|System.Math.Power(Int64 value, Decimal exponent)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość podwójna, wykładnik Int64)|Potęga (wartość, wykładnik)|
|System.Math.Power(Double value, Double exponent)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość podwójna, wykładnik dziesiętny)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość dziesiętna, wykładnik Int64)|Potęga (wartość, wykładnik)|
|System. Math. potęgi (wartość dziesiętna, podwójny wykładnik)|Potęga (wartość, wykładnik)|
|System.Math.Power(Decimal value, Decimal exponent)|Potęga (wartość, wykładnik)|

## <a name="bitwise-operator-mapping"></a>Mapowanie operatora bitowego

|Operator bitowy|Funkcja kanoniczna dla operandów innych niż logiczne|Funkcja kanoniczna dla argumentów operacji typu Boolean|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Operatory bitowe i|BitWiseAnd|OP1 i OP2|
|Operator or|BitWiseOr|OP1 lub OP2|
|Operator NOT bitowego|BitWiseNot|NIE (op)|
|Bitowy operator XOR|BitWiseXor|((OP1 i NOT (OP2)) lub (NOT (OP1) i OP2))|

## <a name="other-mapping"></a>Inne mapowanie

|Metoda|Funkcja kanoniczna|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](linq-to-entities.md)
