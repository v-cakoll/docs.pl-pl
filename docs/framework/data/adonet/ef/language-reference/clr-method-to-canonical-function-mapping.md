---
title: Metody mapowania funkcji Canonical CLR
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 16d447e82959f5ade7210b36dcf9d06bed9c9b00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605720"
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metody mapowania funkcji Canonical CLR

Entity Framework zawiera zestaw funkcje canonical, które implementują funkcjonalność, obejmującą wiele systemów baz danych, takie jak manipulowanie ciągami i funkcji matematycznych. Dzięki temu deweloperzy pod kątem szerokiego zakresu systemów baz danych. Gdy wywoływana z zapytań technologii, takich jak składnik LINQ to Entities, te canonical funkcji są tłumaczone do odpowiedniej funkcji magazynu odpowiednich dla używanego dostawcy. Dzięki temu wywołania funkcji wyrażane w formie wspólnych źródeł danych, zapewniając zapytania spójne środowisko dla źródeł danych. Bitowe AND, OR, NOT, i operatorów XOR również są mapowane na funkcje canonical, gdy argument jest typu liczbowego. Logiczna operandy bitowe AND, OR, NOT, aby uzyskać i operatory XOR logiczne AND, OR, obliczenia i operacje XOR swojego operandu. Aby uzyskać więcej informacji, zobacz [funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).

W przypadku scenariuszy LINQ zapytań względem programu Entity Framework obejmują mapowanie niektórych metod CLR do metody w źródle danych za pomocą funkcji kanonicznej. Wszelkie wywołania metody w składniku LINQ zapytania jednostki, który nie jest jawnie mapowany do kanonicznej funkcji spowoduje w środowisku uruchomieniowym <xref:System.NotSupportedException> zgłaszanego wyjątku.

## <a name="systemstring-method-static-mapping"></a>Metody System.String mapowanie (statyczne)

|Metody System.String (statyczny)|Canonical — funkcja|
|-------------------------------------|------------------------|
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat(Concat(`str0`, `str1`), `str2`)|
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat(Concat(Concat(`str0`, `str1`), `str2`), `str3`)|
|Logiczna Equals (ciąg `a`, ciąg `b`)|= — Operator|
|Wartość logiczna IsNullOrEmpty (ciąg `value`)|(IsNull (`value`)) lub długość (`value`) = 0|
|Op_equality — wartość logiczna (ciąg `a`, ciąg `b`)|= — Operator|
|Op_inequality — wartość logiczna (ciąg `a` , ciąg `b`)|!= - Operator|
|Microsoft.VisualBasic.Strings.Trim(String `str`)|Trim(`str`)|
|Microsoft.VisualBasic.Strings.LTrim(String `str`)|Ltrim(`str`)|
|Microsoft.VisualBasic.Strings.RTrim(String `str`)|Rtrim(`str`)|
|Microsoft.VisualBasic.Strings.Len(String `expression`)|Długość (`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Po lewej stronie (`str`, `Length`)|
|Microsoft.VisualBasic.Strings.Mid(String `str`, Int32 `Start`, Int32 `Length`)|Substring (`str`, `Start`, `Length`)|
|Microsoft.VisualBasic.Strings.Right(String `str`, Int32 `Length`)|Po prawej stronie (`str`, `Length`)|
|Microsoft.VisualBasic.Strings.UCase(String `Value`)|ToUpper (`Value`)|
|Microsoft.VisualBasic.Strings.LCase(String Value)|ToLower (`Value`)|

## <a name="systemstring-method-instance-mapping"></a>Metody System.String (wystąpienie), mapowanie

|Metody System.String (wystąpienie)|Canonical — funkcja|Uwagi|
|---------------------------------------|------------------------|-----------|
|Zawiera atrybut typu wartość logiczna (ciąg `value`)|`this` NP. "%`value`%"|Jeśli `value` nie jest stałą, a następnie mapuje to IndexOf (`this`, `value`) > 0|
|Wartość logiczna EndsWith (String `value`)|`this` LIKE `'`%`value`'|Jeśli `value` nie jest stałą, to mapuje do prawej (`this`, długość (`value`)) = `value`.|
|Wartość logiczna StartsWith (String `value`)|`this` NP. "`value`%"|Jeśli `value` nie jest stałą, a następnie mapuje to IndexOf (`this`, `value`) = 1.|
|Długość|Długość (`this`)||
|Int32 IndexOf (ciąg `value`)|IndexOf (`this`, `value`) - 1||
|System.String Insert(Int32 `startIndex`, String `value`)|Concat (Concat (podciąg (`this`, 1, `startIndex`), `value`), podciąg (`this`, `startIndex`+ 1, długość (`this`)- `startIndex`))||
|System.String Remove(Int32 `startIndex`)|Substring (`this`, 1, `startIndex`)||
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (podciąg (`this`, 1, `startIndex`), podciąg (`this`, `startIndex`  +  `count` + 1, długość (`this`)-(`startIndex` + `count`)))|Usuń (`startIndex`, `count`) jest obsługiwana tylko w przypadku `count` jest liczbą całkowitą większą niż lub równa 0.|
|System.String Replace(String `oldValue`, String `newValue`)|Zastąp (`this`, `oldValue`, `newValue`)||
|System.String Substring(Int32 `startIndex`)|Substring (`this`, `startIndex` + 1, długość (`this`)- `startIndex`)||
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring (`this`, `startIndex` + 1, `length`)||
|System.String ToLower()|ToLower (`this`)||
|System.String ToUpper()|ToUpper (`this`)||
|System.String Trim()|Trim(`this`)||
|System.String TrimEnd(Char[] `trimChars`)|RTrim(`this`)||
|System.String TrimStart(Char[]`trimChars`)|LTrim(`this`)||
|Logiczna Equals (ciąg `value`)|= — Operator||

## <a name="systemdatetime-method-static-mapping"></a>Metody System.DateTime mapowanie (statyczne)

|Metody System.DateTime (statyczny)|Canonical — funkcja|Uwagi|
|---------------------------------------|------------------------|-----------|
|Logiczna Equals (daty/godziny `t1`, daty/godziny `t2`)|= — Operator||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Op_equality — wartość logiczna (daty/godziny `d1`, daty/godziny `d2`)|= — Operator||
|Op_greaterthan — wartość logiczna (daty/godziny `t1`, daty/godziny `t2`)|> operator||
|Op_greaterthanorequal — wartość logiczna (daty/godziny `t1`, daty/godziny `t2`)|> = — operator||
|Op_inequality — wartość logiczna (daty/godziny `t1`, daty/godziny `t2`)|!= - Operator||
|Op_lessthan — wartość logiczna (daty/godziny `t1`, daty/godziny `t2`)|< — operator||
|Op_lessthanorequal — wartość logiczna (daty/godziny `t1`, daty/godziny `t2`)|< = — operator||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval` jako DateInterval, \_<br /><br /> ByVal `DateValue` jako wartość DateTime, \_<br /><br /> Opcjonalne ByVal `FirstDayOfWeekValue` jako FirstDayOfWeek = stałej VbSunday, \_<br /><br /> Opcjonalne ByVal `FirstWeekOfYearValue` jako FirstWeekOfYear = VbFirstJan1 \_<br /><br /> ) Jako liczba całkowita||Zobacz sekcję Funkcja DatePart, aby uzyskać więcej informacji.|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year()||
|Microsoft.VisualBasic.DateAndTime.Month(DateTime `TimeValue`)|Month()||
|Microsoft.VisualBasic.DateAndTime.Day (daty/godziny `TimeValue`)|Day()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|MINUTE()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Second()||

## <a name="systemdatetime-method-instance-mapping"></a>Metody System.DateTime (wystąpienie), mapowanie

|System.DateTime method (instance)|Canonical — funkcja|
|-----------------------------------------|------------------------|
|Logiczna Equals (daty/godziny `value`)|= — Operator|
|Dzień|Dzień (`this`)|
|Godzina|Godzina (`this`)|
|Millisecond|Millisecond(`this`)|
|Minuta|Minuty (`this`)|
|Miesiąc|Miesiąc (`this`)|
|Sekunda|Drugi (`this`)|
|Rok|Rok (`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>Metody System.DateTimeOffset (wystąpienie), mapowanie

Mapowanie wyświetlane dla `get` metody na liście właściwości.

|System.DateTimeOffset method (instance)|Canonical — funkcja|Uwagi|
|-----------------------------------------------|------------------------|-----------|
|Dzień|Dzień (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Godzina|Godzina (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Millisecond|Millisecond(`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Minuta|Minuty (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Miesiąc|Miesiąc (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Sekunda|Drugi (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Rok|Rok (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|

> [!NOTE]
> <xref:System.DateTimeOffset.Equals%2A> Metoda zwraca `true` Jeśli porównany z certyfikatami <xref:System.DateTimeOffset> obiekty są równe; `false` inaczej. <xref:System.DateTimeOffset.CompareTo%2A> Metoda zwróci wartość 0, 1 lub -1 w zależności od tego, czy porównany z certyfikatami <xref:System.DateTimeOffset> obiekt jest taki sam, większa lub mniejsza niż odpowiednio.

## <a name="systemdatetimeoffset-method-static-mapping"></a>Metody System.DateTimeOffset mapowanie (statyczne)

Mapowanie wyświetlane dla `get` metody na liście właściwości.

|Metody System.DateTimeOffset (statyczny)|Canonical — funkcja|Uwagi|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Nie jest obsługiwane dla programu SQL Server 2005.|

## <a name="systemtimespan-method-instance-mapping"></a>System.TimeSpan Method (Instance) Mapping

Mapowanie wyświetlane dla `get` metody na liście właściwości.

|Metody System.TimeSpan (wystąpienie)|Canonical — funkcja|Uwagi|
|-----------------------------------------|------------------------|-----------|
|godz.|Godzina (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|MS|Millisecond(`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|Minuty|Minuty (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|
|sekundy|Drugi (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|

> [!NOTE]
> <xref:System.TimeSpan.Equals%2A> Metoda zwraca `true` Jeśli porównany z certyfikatami <xref:System.TimeSpan> obiekty są równe; `false` inaczej. <xref:System.TimeSpan.CompareTo%2A> Metoda zwróci wartość 0, 1 lub -1 w zależności od tego, czy porównany z certyfikatami <xref:System.TimeSpan> obiekt jest taki sam, większa lub mniejsza niż odpowiednio.

### <a name="datepart-function"></a>Funkcja DatePart

`DatePart` Funkcji jest mapowany na jeden z kilku różnych funkcje canonical, w zależności od wartości `Interval`. W poniższej tabeli przedstawiono mapowania kanonicznej funkcji dla obsługiwane wartości równych `Interval`:

|Wartość interwału|Canonical — funkcja|
|--------------------|------------------------|
|DateInterval.Year|Year()|
|DateInterval.Month|Month()|
|DateInterval.Day|Day()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|MINUTE()|
|DateInterval.Second|Second()|

## <a name="mathematical-function-mapping"></a>Mapowanie funkcji matematycznych

|CLR — metoda|Canonical — funkcja|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|CEILING (`d`)|
|System.Decimal.Floor(Decimal `d`)|FLOOR (`d`)|
|System.Decimal.Round(Decimal `d`)|ROUND (`d`)|
|System.Math.Ceiling(Decimal `d`)|CEILING (`d`)|
|System.Math.Floor(Decimal `d`)|FLOOR (`d`)|
|System.Math.Round(Decimal `d`)|ROUND (`d`)|
|System.Math.Ceiling(Double `a`)|CEILING (`a`)|
|System.Math.Floor(Double `a`)|FLOOR (`a`)|
|System.Math.Round (podwójny `a`)|ROUND (`a`)|
|System.Math.Round(Double value, Int16 digits)|Zaokrąglij (wartość cyfr)|
|System.Math.Round(Double value, Int32 digits)|Zaokrąglij (wartość cyfr)|
|System.Math.Round(Decimal value, Int16 digits)|Zaokrąglij (wartość cyfr)|
|System.Math.Round(Decimal value, Int32, digits)|Zaokrąglij (wartość cyfr)|
|System.Math.Abs(Int16 value)|ABS(Value)|
|System.Math.Abs(Int32 value)|ABS(Value)|
|System.Math.Abs(Int64 value)|ABS(Value)|
|System.Math.Abs(Byte value)|ABS(Value)|
|System.Math.Abs(Single value)|ABS(Value)|
|System.Math.Abs(Double value)|ABS(Value)|
|System.Math.Abs(Decimal value)|ABS(Value)|
|System.Math.Truncate(Double value, Int16 digits)|Obetnij (wartość cyfr)|
|System.Math.Truncate(Double value, Int32 digits)|Obetnij (wartość cyfr)|
|System.Math.Truncate(Decimal value, Int16 digits)|Obetnij (wartość cyfr)|
|System.Math.Truncate(Decimal value, Int32 digits)|Obetnij (wartość cyfr)|
|System.Math.Power(Int32 value, Int64 exponent)|Zasilania (wartość wykładnika)|
|System.Math.Power (wartość Int32 wykładnik Double)|Zasilania (wartość wykładnika)|
|System.Math.Power (wartość Int32, wykładnik dziesiętna)|Zasilania (wartość wykładnika)|
|System.Math.Power(Int64 value, Int64 exponent)|Zasilania (wartość wykładnika)|
|System.Math.Power (wartość Int64 wykładnik Double)|Zasilania (wartość wykładnika)|
|System.Math.Power(Int64 value, Decimal exponent)|Zasilania (wartość wykładnika)|
|System.Math.Power (podwójna wartość, Int64 wykładnik)|Zasilania (wartość wykładnika)|
|System.Math.Power(Double value, Double exponent)|Zasilania (wartość wykładnika)|
|System.Math.Power (podwójna wartość, wykładnik dziesiętna)|Zasilania (wartość wykładnika)|
|System.Math.Power (wartość dziesiętną, Int64 wykładnik)|Zasilania (wartość wykładnika)|
|System.Math.Power (dziesiętna wartość i wykładnik Double)|Zasilania (wartość wykładnika)|
|System.Math.Power(Decimal value, Decimal exponent)|Zasilania (wartość wykładnika)|

## <a name="bitwise-operator-mapping"></a>Bitowy Operator mapowania

|Bitowy operator|Kanonicznej funkcji w przypadku argumentów operacji inne niż logiczne|Kanonicznej funkcji w przypadku argumentów operacji logicznych|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Bitowy operator AND|BitWiseAnd|op1 op2 i|
|Bitowy operator OR|BitWiseOr|op1 OR op2|
|Bitowy NOT operator|BitWiseNot|NOT(OP)|
|Bitowy operator XOR|BitWiseXor|((op1 NOT(op2)) i OR (NOT(op1) i op2))|

## <a name="other-mapping"></a>Inne mapowanie

|Metoda|Canonical — funkcja|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
