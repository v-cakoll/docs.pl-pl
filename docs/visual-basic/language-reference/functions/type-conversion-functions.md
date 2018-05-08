---
title: Funkcje konwersji typu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c9222bdb31f4fd7c792d5a50c100067e29e9d537
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-conversion-functions-visual-basic"></a>Funkcje konwersji typu (Visual Basic)
Te funkcje są skompilowaną wbudowaną, co oznacza, że kod konwersji jest częścią kodu, który wylicza wartość wyrażenia. Czasami nie istnieje żadne wywołanie procedury do wykonania konwersji, co zwiększa wydajność. Każda funkcja przekształca wyrażenie określonego typu danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a>Część  
 `expression`  
 Wymagana. Dowolne wyrażenie typu źródła danych.  
  
## <a name="return-value-data-type"></a>Zwraca typ danych wartości  
 Nazwa funkcji określa typ danych wartości, która zwraca, jak pokazano w poniższej tabeli.  
  
|Nazwa funkcji|Zwracany typ danych|Zakres dla `expression` argumentu|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Wszystkie prawidłowe `Char` lub `String` lub wyrażenia liczbowego.|  
|`CByte`|[Byte, typ danych](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 do 255 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CChar`|[Char, typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)|Wszystkie prawidłowe `Char` lub `String` wyrażenia, tylko pierwszy znak `String` konwersji; możliwe wartości od 0 do 65535 (bez znaku).|  
|`CDate`|[Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Wszystkie prawidłowe reprezentacja daty i godziny.|  
|`CDbl`|[Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych; 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 do wartości dodatnie.|  
|`CDec`|[Decimal, typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79,228,162,514,264,337,593,543,950,335 162 514 liczb, czyli liczby bez miejsc dziesiętnych. W przypadku numerów 28 miejsc dziesiętnych zakres jest +/-7.9228162514264337593543950335. Najmniejsza możliwa liczba niezerowa to 0,0000000000000000000000000001 (+/-1E-28).|  
|`CInt`|[Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)|-2,147,483,648 do 2 147 483 647; są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CLng`|[Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)|-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807; są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CObj`|[Object, typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md)|Dowolne prawidłowe wyrażenie.|  
|`CSByte`|[SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|-128 do 127; są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CShort`|[Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)|-32 768 do 32 767; są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CSng`|[Single, typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38 do - 1, 401298E-45 dla wartości ujemnych; 1, 401298E-45 za pośrednictwem 3.402823E + 38 dla wartości dodatnie.|  
|`CStr`|[String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)|Zwraca `CStr` są zależne od `expression` argumentu. Zobacz [zwracane wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|od 0 do 4 294 967 295 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CULng`|[ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|od 0 do 18,446,744,073,709,551,615 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup>|  
|`CUShort`|[UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|od 0 do 65 535 (bez znaku); są zaokrąglane ułamkowych części. <sup>1</sup>|  
  
 <sup>1</sup> ułamkowych części mogą podlegać specjalny typ zaokrąglania wywołane *zaokrąglenie do zaokrąglania*. Aby uzyskać więcej informacji, zobacz "Uwagi".  
  
## <a name="remarks"></a>Uwagi  
 Jako regułę, należy używać funkcje konwersji typu Visual Basic, zamiast metod .NET Framework takie jak `ToString()`, albo na <xref:System.Convert> klasy lub na poszczególnych typ struktury lub klasy. Funkcje Visual Basic są przeznaczone do optymalnego interakcji z kodu języka Visual Basic, a także umożliwiają kod źródłowy krótsze i łatwiejsze do odczytu. Ponadto metody konwersji .NET Framework nie zawsze utworzyć takie same wyniki jako funkcje języka Visual Basic, na przykład podczas konwertowania `Boolean` do `Integer`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Koercja.** Ogólnie rzecz biorąc można użyć funkcji konwersji typu danych konwersji wynik operacji do określonego typu danych niż domyślny typ danych. Na przykład użyć `CDec` wymusić dziesiętną arytmetyczne w przypadkach, gdy pojedynczej precyzji, podwójnej precyzji lub liczba całkowita arytmetyczne zwykle nastąpiłoby.  
  
-   **Konwersje nie powiodło się.** Jeśli `expression` przekazany do funkcji jest poza zakresem typu danych, których ma zostać przekonwertowany, <xref:System.OverflowException> występuje.  
  
-   **Ułamkowych części.** Podczas konwertowania wartości nonintegral typem całkowitym typ, liczbę całkowitą funkcji konwersji (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, i `CUShort`) Usuń ułamkowych części i zaokrąglona do najbliższej liczby całkowitej wartość.  
  
     Jeśli część ułamkowa jest dokładnie 0,5, funkcje konwersji całkowitą zaokrąglona do najbliższej parzystej liczby całkowitej. Na przykład 0,5 zaokrągla wartość 0 i w wersji 1.5 i 2.5, który zarówno zaokrąglona do 2. Jest to czasem nazywane *zaokrąglenie do zaokrąglania*, a jej celem jest kompensacji odchylenia, który może narastać, dodając takiej liczby razem.  
  
     `CInt` i `CLng` różnią się od <xref:Microsoft.VisualBasic.Conversion.Int%2A> i <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkcji, które truncate, zamiast zaokrąglona ułamkową część liczby. Ponadto `Fix` i `Int` zawsze zwraca wartość typu danych podczas przemieszczania w.  
  
-   **Data/Godzina konwersji.** Użyj <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkcji, aby określić, jeśli można przekonwertować wartości na datę i godzinę. `CDate` rozpoznaje literałów dat i godzin, ale wartości liczbowych nie. Aby przekonwertować Visual Basic 6.0 `Date` do wartości `Date` wartość w języku Visual Basic 2005 lub nowszym, można użyć <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> — metoda.  
  
-   **Neutralna wartości daty/godziny.** [Date — typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md) zawsze zawiera informacje zarówno datę i godzinę. W celu konwersji typu, Visual Basic uważa 1/1/0001 (1 stycznia 1 roku) *neutralne wartość* daty i 00:00:00 (północ) jako neutralny wartość po raz. W przypadku przekonwertowania `Date` wartość na ciąg `CStr` nie ma wartości neutralne w ciągu wynikowym. Na przykład, jeśli przekonwertujesz `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 AM"; informacje o dacie jest pomijane. Jednak informacje o dacie jest nadal znajdują się w oryginalnym `Date` wartości i może zostać przywrócona z funkcji takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkcji.  
  
-   **Czułość kultury.** Funkcje konwersji typu obejmującego ciągów wykonaj konwersje w oparciu o bieżące ustawienia kultury dla aplikacji. Na przykład `CDate` rozpoznaje formaty daty zgodnie z ustawieniem ustawień regionalnych systemu. Należy podać dzień, miesiąc i rok w odpowiedniej kolejności dla ustawień regionalnych użytkownika lub daty może nie być prawidłowo interpretowane. Nie rozpoznano formatu daty długiej, jeśli zawiera ciąg dzień tygodnia, takie jak "Środa".  
  
     Jeśli chcesz przekonwertować z reprezentacji ciągu wartości w formacie innym niż określony przez ustawienia regionalne lub nie można użyć funkcje konwersji typu Visual Basic. Aby to zrobić, użyj `ToString(IFormatProvider)` i `Parse(String, IFormatProvider)` metod z typem tej wartości. Na przykład użyć <xref:System.Double.Parse%2A?displayProperty=nameWithType> podczas konwertowania ciągu na `Double`i użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na ciąg.  
  
## <a name="ctype-function"></a>CType — Funkcja  
 [CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md) przyjmuje drugi argument, `typename`i przekształca wynik dane `expression` do `typename`, gdzie `typename` może być typu danych, struktury, klasy lub interfejsu, do którego istnieje prawidłowa konwersja.  
  
 Porównanie `CType` z innych typów słowa kluczowe konwersji, zobacz [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) i [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>Przykład CBool  
 W poniższym przykładzie użyto `CBool` funkcji konwersji wyrażenia do `Boolean` wartości. Jeśli wyrażenie ma wartość różną od zera `CBool` zwraca `True`; w przeciwnym razie zwraca `False`.  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>Przykład CByte  
 W poniższym przykładzie użyto `CByte` funkcji konwersji wyrażenia do `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>Przykład CChar  
 W poniższym przykładzie użyto `CChar` funkcji konwersji pierwszego znaku `String` wyrażenie `Char` typu.  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 Argument wejściowy `CChar` musi być typu danych `Char` lub `String`. Nie można użyć `CChar` do konwertowania wartości na znak, ponieważ `CChar` nie może akceptować dane typu liczbowego. Poniższy przykład uzyskuje liczba reprezentująca punkt kodu (kod znaku) i konwertuje ją na odpowiedni znak. Używa <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkcji, aby uzyskać ciąg cyfr, `CInt` można przekonwertować ciągu na typ `Integer`, i `ChrW` do konwertowanie liczby na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>Przykład CDate  
 W poniższym przykładzie użyto `CDate` funkcji konwersji ciągów na `Date` wartości. Ogólnie rzecz biorąc kodować dat i godzin jako ciągi (jak pokazano w tym przykładzie) nie jest zalecane. Użyj literałów dat i godzin, takie jak #Feb 12, 1969 # i # 4:45:23 PM #, zamiast tego.  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>Przykład CDbl  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>Przykład CDec  
 W poniższym przykładzie użyto `CDec` funkcji konwersji wartość liczbową `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>Przykład CInt  
 W poniższym przykładzie użyto `CInt` funkcji można przekonwertować wartości na `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a>Przykład CLng  
 W poniższym przykładzie użyto `CLng` funkcji można przekonwertować wartości na `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>Przykład CObj  
 W poniższym przykładzie użyto `CObj` funkcji konwersji wartość liczbową `Object`. `Object` Samej zmiennej zawierają tylko wskaźnik 4 bajtowych, która wskazuje na `Double` wartość przypisana do niego.  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>Przykład CSByte  
 W poniższym przykładzie użyto `CSByte` funkcji konwersji wartość liczbową `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>Przykład CShort  
 W poniższym przykładzie użyto `CShort` funkcji konwersji wartość liczbową `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>Przykład CSng  
 W poniższym przykładzie użyto `CSng` funkcji można przekonwertować wartości na `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>Przykład CStr  
 W poniższym przykładzie użyto `CStr` funkcji konwersji wartość liczbową `String`.  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 W poniższym przykładzie użyto `CStr` funkcji konwersji `Date` wartości do `String` wartości.  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr` zawsze renderuje `Date` wartość w standardowym formacie krótkiej dla bieżących ustawień regionalnych, na przykład "15-6-2003 4:35:47 PM". Jednak `CStr` pomija *niezależnym od wartości* z 1/1/0001 daty i 00:00:00 czasu.  
  
 Aby uzyskać więcej szczegółów na wartości zwracanych przez `CStr`, zobacz [zwracać wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Przykład CUInt  
 W poniższym przykładzie użyto `CUInt` funkcji konwersji wartość liczbową `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>Przykład CULng  
 W poniższym przykładzie użyto `CULng` funkcji konwersji wartość liczbową `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>Przykład CUShort  
 W poniższym przykładzie użyto `CUShort` funkcji konwersji wartość liczbową `UShort`.  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [Funkcje konwersji](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
