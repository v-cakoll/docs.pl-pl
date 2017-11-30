---
title: Metody mapowania kanonicznej funkcji CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5d1e6a1cc362663be3aa6c6084f658eba25dfe54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metody mapowania kanonicznej funkcji CLR
Entity Framework zawiera zestaw kanonicznej funkcji, które implementuje funkcje, które są wspólne w wielu systemach bazy danych, takich jak funkcje matematyczne i manipulowanie ciągami. Pozwala to deweloperom target szeroką gamę systemów bazy danych. Przy wywołaniach z podczas badania technologii, takich jak LINQ to Entities, te kanonicznej funkcji są tłumaczone na poprawną odpowiedniego magazynu dla używany dostawca. Dzięki temu wywołania funkcji wyrażane w formie wspólnej między źródłami danych, zapewniając środowisko spójne zapytania między źródłami danych. Bitowe AND, OR, NOT i XOR operatory są również mapowany na funkcje canonical, gdy argument jest typu liczbowego. Dla logiczna operandy bitowe AND, OR, NOT, a nie obliczeniowe XOR operatorów logicznych AND, OR i ich operandami XOR operacji. Aby uzyskać więcej informacji, zobacz [kanonicznej funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
 W przypadku scenariuszy LINQ zapytań dotyczących programu Entity Framework obejmują niektórych metod CLR mapowania do metod w źródle danych za pomocą funkcji kanonicznej. Wszystkie wywołania metody w składniku LINQ do jednostek zapytania, które nie są jawnie przypisane do funkcji kanonicznej spowoduje w środowisku uruchomieniowym <xref:System.NotSupportedException> zgłaszanego wyjątku.  
  
## <a name="systemstring-method-static-mapping"></a>Mapowanie (statyczny) System.String — metoda  
  
|Metoda System.String (statyczny)|Canonical — funkcja|  
|-------------------------------------|------------------------|  
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat (Concat (Concat (`str0`, `str1`), `str2`), `str3`)|  
|Logiczna Equals (ciąg `a`, ciąg `b`)|= — Operator|  
|Wartość logiczna IsNullOrEmpty (ciąg `value`)|(IsNull (`value`)) lub długość (`value`) = 0|  
|Wartość logiczna op_Equality (ciąg `a`, ciąg `b`)|= — Operator|  
|Wartość logiczna op_Inequality (ciąg `a` , ciąg `b`)|!= - Operator|  
|Microsoft.VisualBasic.Strings.Trim (ciąg `str`)|Przytnij (`str`)|  
|Microsoft.VisualBasic.Strings.LTrim (ciąg `str`)|Przytp (`str`)|  
|Microsoft.VisualBasic.Strings.RTrim (ciąg `str`)|Przytk (`str`)|  
|Microsoft.VisualBasic.Strings.Len (ciąg `expression`)|Długość (`expression`)|  
|Microsoft.VisualBasic.Strings.Left (ciąg `str`, Int32 `Length`)|Od lewej (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.Mid (ciąg `str`, Int32 `Start`, Int32 `Length`)|Substring (`str`, `Start`, `Length`)|  
|Microsoft.VisualBasic.Strings.Right (ciąg `str`, Int32 `Length`)|Prawa (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.UCase (ciąg `Value`)|ToUpper (`Value`)|  
|Microsoft.VisualBasic.Strings.LCase (ciąg)|ToLower (`Value`)|  
  
## <a name="systemstring-method-instance-mapping"></a>Metoda System.String (wystąpieniem) mapowania  
  
|Metoda System.String (wystąpieniem)|Canonical — funkcja|Uwagi|  
|---------------------------------------|------------------------|-----------|  
|Zawiera wartość logiczna (ciąg `value`)|`this`PODOBNIE JAK ' %`value`% "|Jeśli `value` nie jest stałą, a następnie mapuje to IndexOf (`this`, `value`) > 0.|  
|Wartość logiczna EndsWith (String `value`)|`this`PODOBNIE JAK `'` % `value`"|Jeśli `value` nie jest stałą, to mapuje do prawej (`this`, długość (`value`)) = `value`.|  
|Wartość logiczna StartsWith (String `value`)|`this`TAKIE JAK "`value`%"|Jeśli `value` nie jest stałą, a następnie mapuje to IndexOf (`this`, `value`) = 1.|  
|długość|Długość (`this`)||  
|Int32 IndexOf (ciąg `value`)|IndexOf (`this`, `value`) - 1||  
|System.String Insert(Int32 `startIndex`, String `value`)|Concat (Concat (podciąg (`this`, 1, `startIndex`), `value`), podciąg (`this`, `startIndex`+ 1, długość (`this`)- `startIndex`))||  
|System.String Remove(Int32 `startIndex`)|Substring (`this`, 1, `startIndex`)||  
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (podciąg (`this`, 1, `startIndex`), podciąg (`this`, `startIndex`  +  `count` + 1, długość (`this`)-(`startIndex` + `count`)))|Usuń (`startIndex`, `count`) jest obsługiwana tylko w przypadku `count` jest liczba całkowita większa lub równa 0.|  
ystem. Zastąp ciąg (String `oldValue`, ciąg `newValue`)|Zastąp (`this`, `oldValue`, `newValue`)||  
|System.String Substring(Int32 `startIndex`)|Substring (`this`, `startIndex` + 1, długość (`this`)- `startIndex`)||  
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring (`this`, `startIndex` + 1, `length`)||  
|System.String ToLower()|ToLower (`this`)||  
|System.String ToUpper()|ToUpper (`this`)||  
|System.String Trim()|Przytnij (`this`)||  
|System.String TrimEnd(Char[] `trimChars`)|Przytk (`this`)||  
|System.String TrimStart(Char[]`trimChars`)|Przytp (`this`)||  
|Logiczna Equals (ciąg `value`)|= — Operator||  
  
## <a name="systemdatetime-method-static-mapping"></a>Mapowanie (statyczny) System.DateTime — metoda  
  
|Metoda System.DateTime (statyczny)|Canonical — funkcja|Uwagi|  
|---------------------------------------|------------------------|-----------|  
|Logiczna Equals (DateTime `t1`, DateTime `t2`)|= — Operator||  
|System.DateTime.Now|CurrentDateTime()||  
|System.DateTime.UtcNow|CurrentUtcDateTime()||  
|Wartość logiczna op_Equality (DateTime `d1`, DateTime `d2`)|= — Operator||  
|Wartość logiczna op_GreaterThan (DateTime `t1`, DateTime `t2`)|> — Operator||  
|Wartość logiczna op_GreaterThanOrEqual (DateTime `t1`, DateTime `t2`)|>= — Operator||  
|Wartość logiczna op_Inequality (DateTime `t1`, DateTime `t2`)|!= - Operator||  
|Wartość logiczna op_LessThan (DateTime `t1`, DateTime `t2`)|< — Operator||  
|Wartość logiczna op_LessThanOrEqual (DateTime `t1`, DateTime `t2`)|<= — Operator||  
|Microsoft.VisualBasic.DateAndTime.DatePart (_<br /><br /> ByVal `Interval` jako DateInterval,\_<br /><br /> ByVal `DateValue` jako element DateTime,\_<br /><br /> Opcjonalne ByVal `FirstDayOfWeekValue` jako FirstDayOfWeek = stałej VbSunday,\_<br /><br /> Opcjonalne ByVal `FirstWeekOfYearValue` jako Pierwszy_tydzień_roku = VbFirstJan1\_<br /><br /> ) W postaci liczby całkowitej.||Zobacz sekcję Funkcja DatePart, aby uzyskać więcej informacji.|  
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||  
|Microsoft.VisualBasic.DateAndTime.Year (DateTime `TimeValue`)|Year()||  
|Microsoft.VisualBasic.DateAndTime.Month (DateTime `TimeValue`)|Month()||  
icrosoft. VisualBasic.DateAndTime.Day (DateTime `TimeValue`)|Day()||  
|Microsoft.VisualBasic.DateAndTime.Hour (DateTime `TimeValue`)|Hour()||  
|Microsoft.VisualBasic.DateAndTime.Minute (DateTime `TimeValue`)|MINUTE()||  
|Microsoft.VisualBasic.DateAndTime.Second (DateTime `TimeValue`)|Second()||  
  
## <a name="systemdatetime-method-instance-mapping"></a>Metoda System.DateTime (wystąpieniem) mapowania  
  
|Metoda System.DateTime (wystąpieniem)|Canonical — funkcja|  
|-----------------------------------------|------------------------|  
|Logiczna Equals (DateTime `value`)|= — Operator|  
|Dzień|Dzień (`this`)|  
|Godzina|Godzina (`this`)|  
|Milisekundy|Milisekundy (`this`)|  
|Minuta|Minuty (`this`)|  
|Miesiąc|Miesiąc (`this`)|  
|Sekunda|Drugi (`this`)|  
|Rok|Roku (`this`)|  
  
## <a name="systemdatetimeoffset-method-instance-mapping"></a>Metoda System.DateTimeOffset (wystąpieniem) mapowania  
 Mapowanie wyświetlany dla `get` metody właściwości z listy.  
  
|Metoda System.DateTimeOffset (wystąpieniem)|Canonical — funkcja|Uwagi|  
|-----------------------------------------------|------------------------|-----------|  
|Dzień|Dzień (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Godzina|Godzina (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Milisekundy|Milisekundy (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Minuta|Minuty (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Miesiąc|Miesiąc (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Sekunda|Drugi (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Rok|Roku (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
  
> [!NOTE]
>  <xref:System.DateTimeOffset.Equals%2A> Metoda zwraca `true` Jeśli porównany z certyfikatami <xref:System.DateTimeOffset> obiekty są takie same; `false` inaczej. <xref:System.DateTimeOffset.CompareTo%2A> Metoda zwraca wartość 0, 1 lub -1 w zależności od tego, czy porównany z certyfikatami <xref:System.DateTimeOffset> obiekt jest taki sam, większa lub mniejsza niż odpowiednio.  
  
## <a name="systemdatetimeoffset-method-static-mapping"></a>Mapowanie (statyczny) System.DateTimeOffset — metoda  
 Mapowanie wyświetlany dla `get` metody właściwości z listy.  
  
|Metoda System.DateTimeOffset (statyczny)|Canonical — funkcja|Uwagi|  
|---------------------------------------------|------------------------|-----------|  
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Nie jest obsługiwane dla programu SQL Server 2005.|  
  
## <a name="systemtimespan-method-instance-mapping"></a>Obiekt System.TimeSpan — metoda (wystąpieniem) mapowania  
 Mapowanie wyświetlany dla `get` metody właściwości z listy.  
  
|Obiekt System.TimeSpan — metoda (wystąpieniem)|Canonical — funkcja|Uwagi|  
|-----------------------------------------|------------------------|-----------|  
|Godziny|Godzina (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|w milisekundach|Milisekundy (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|minut|Minuty (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
|Sekund|Drugi (`this`)|Nie jest obsługiwane dla programu SQL Server 2005.|  
  
> [!NOTE]
>  <xref:System.TimeSpan.Equals%2A> Metoda zwraca `true` Jeśli porównany z certyfikatami <xref:System.TimeSpan> obiekty są takie same; `false` inaczej. <xref:System.TimeSpan.CompareTo%2A> Metoda zwraca wartość 0, 1 lub -1 w zależności od tego, czy porównany z certyfikatami <xref:System.TimeSpan> obiekt jest taki sam, większa lub mniejsza niż odpowiednio.  
  
### <a name="datepart-function"></a>Funkcja DatePart  
 `DatePart` Funkcji jest mapowany na jedną z kilku różnych funkcji kanonicznej, w zależności od wartości `Interval`. W poniższej tabeli przedstawiono mapowanie funkcji kanonicznej dla obsługiwanych wartości `Interval`:  
  
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
|System.Decimal.Ceiling (dziesiętne `d`)|CEILING (`d`)|  
|System.Decimal.Floor (dziesiętne `d`)|FLOOR (`d`)|  
|System.Decimal.Round (dziesiętne `d`)|ROUND (`d`)|  
|System.Math.Ceiling (dziesiętne `d`)|CEILING (`d`)|  
|System.Math.Floor (dziesiętne `d`)|FLOOR (`d`)|  
|System.Math.Round (dziesiętne `d`)|ROUND (`d`)|  
|System.Math.Ceiling (dwa razy `a`)|CEILING (`a`)|  
|System.Math.Floor (dwa razy `a`)|FLOOR (`a`)|  
|System.Math.Round (dwa razy `a`)|ROUND (`a`)|  
|System.Math.Round (Double wartość, Int16 cyfr)|Zaokrąglij (wartość cyfr)|  
|System.Math.Round (Double wartość, Int32 cyfr)|Zaokrąglij (wartość cyfr)|  
|System.Math.Round (wartość dziesiętna, Int16 cyfr)|Zaokrąglij (wartość cyfr)|  
|System.Math.Round (cyfry dziesiętnej, Int32)|Zaokrąglij (wartość cyfr)|  
|System.Math.Abs (wartości Int16)|ABS(Value)|  
|System.Math.Abs (wartości Int32)|ABS(Value)|  
|System.Math.Abs (wartości Int64)|ABS(Value)|  
|System.Math.Abs (wartość bajtu)|ABS(Value)|  
|System.Math.Abs (pojedynczą wartość)|ABS(Value)|  
|System.Math.Abs (wartości Double)|ABS(Value)|  
|System.Math.Abs (dziesiętna wartość)|ABS(Value)|  
|System.Math.Truncate (Double wartość, Int16 cyfr)|TRUNCATE (wartość cyfr)|  
|System.Math.Truncate (Double wartość, Int32 cyfr)|TRUNCATE (wartość cyfr)|  
|System.Math.Truncate (wartość dziesiętna, Int16 cyfr)|TRUNCATE (wartość cyfr)|  
|System.Math.Truncate (wartość dziesiętna, Int32 cyfr)|TRUNCATE (wartość cyfr)|  
|System.Math.Power (wartości Int32, Int64 wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartości Int32 wykładnik podwójny)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartości Int32, Decimal wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartości Int64, Int64 wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartości Int64 wykładnik podwójny)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartości Int64, Decimal wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (Double wartość, Int64 wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (podwojenie, Double wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (Double wartość, Decimal wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartość dziesiętna, Int64 wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartość dziesiętna, Double wykładnik)|Zasilania (wartość, wykładnika)|  
|System.Math.Power (wartość dziesiętna, Decimal wykładnik)|Zasilania (wartość, wykładnika)|  
  
## <a name="bitwise-operator-mapping"></a>Bitowy Operator mapowania  
  
|Bitowy operator|Kanonicznej funkcji w przypadku argumentów operacji inne niż logiczne|Funkcji kanonicznej dla argumentów logicznych|  
|----------------------|--------------------------------------------------|---------------------------------------------|  
|Bitowy operator AND|BitWiseAnd|op1 op2 i|  
|Bitowy operator OR|BitWiseOr|op1 OR op2|  
|Operator NOT — operator|BitWiseNot|NOT(OP)|  
|Bitowy operator XOR|BitWiseXor|((op1 NOT(op2)) i OR (NOT(op1) i op2))|  
  
## <a name="other-mapping"></a>Inne mapowania  
  
|Metoda|Canonical — funkcja|  
|------------|------------------------|  
|Guid.NewGuid()|NewGuid()|  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do jednostek](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
