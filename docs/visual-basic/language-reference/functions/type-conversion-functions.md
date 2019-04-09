---
title: Funkcje konwersji typu (Visual Basic)
ms.date: 10/24/2018
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
ms.openlocfilehash: 56dad921b2900061dbe2db0d8f1faaf759641f87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148138"
---
# <a name="type-conversion-functions-visual-basic"></a>Funkcje konwersji typu (Visual Basic)
Te funkcje są skompilowany w tekście, co oznacza, że kod konwersji jest częścią kodu, który oblicza wyrażenie. Czasami jest Brak wywołania do procedury wykonywania konwersji, co zwiększa wydajność. Każda funkcja przekształca wynik wyrażenia na określony typ danych.  
  
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
 Nazwa funkcji określa typ danych wartości, która zwraca wartość, jak pokazano w poniższej tabeli.  
  
|Nazwa funkcji|Zwracany typ danych|Zakres dla `expression` argumentu|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Typ logiczny danych (boolowski)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Dowolne, prawidłowe `Char` lub `String` lub wyrażenia liczbowego.|  
|`CByte`|[Byte — Typ danych](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) za pośrednictwem <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaku); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych, konwersja bajtów z `CByte` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
|`CChar`|[Char — Typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)|Dowolne, prawidłowe `Char` lub `String` wyrażenie; tylko pierwszy znak `String` jest konwertowany; możliwe wartości od 0 do 65535 (bez znaku).|  
|`CDate`|[Date — Typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Wszelkie Nieprawidłowa reprezentacja daty i godziny.|  
|`CDbl`|[Double — typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych; 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 dla wartości dodatnich.|  
|`CDec`|[Decimal — Typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79,228,162,514,264,337,593,543,950,335 numerów skalowanych na zero oznacza to, liczby bez miejsc dziesiętnych. W przypadku liczb 28 miejsc dziesiętnych zakres jest +/-7.9228162514264337593543950335. Najmniejsza możliwa liczba różna od zera jest 0,0000000000000000000000000001 (+/-1E-28).|  
|`CInt`|[Integer — Typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) za pośrednictwem <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); ułamkowe są zaokrąglane.<sup> 1</sup> <br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych, konwersja liczby całkowitej z `CInt` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład. |  
|`CLng`|[Long — Typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) za pośrednictwem <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych, konwersja 64-bitową liczbę całkowitą z `CLng` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
|`CObj`|[Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md)|Dowolne prawidłowe wyrażenie.|  
|`CSByte`|[SByte — Typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (od -128) za pośrednictwem <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych Aby konwersja bajt oznaczony za pomocą `CSByte` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
|`CShort`|[Short — typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) za pośrednictwem <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych, konwersja 16-bitową liczbę całkowitą z `CShort` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
|`CSng`|[Single — Typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38-do - 1, 401298E-45 dla wartości ujemnych; 1, 401298E-45 za pośrednictwem 3.402823E + 38 dla wartości dodatnich.|  
|`CStr`|[Typ danych ciągu](../../../visual-basic/language-reference/data-types/string-data-type.md)|Zwraca `CStr` zależą od `expression` argumentu. Zobacz [zwracane wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[UInteger — Typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) za pośrednictwem <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaku); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych do konwersji liczb całkowitych bez znaku z `CUInt` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
|`CULng`|[ULong — Typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) za pośrednictwem <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (bez znaku); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych, konwersja niepodpisane długa liczba całkowita z `CULng` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
|`CUShort`|[UShort — Typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) za pośrednictwem <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaku); ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od 15.8 Visual Basic, Visual Basic optymalizację wydajności zmiennoprzecinkowych na liczbę całkowitą bez znaku 16-bitowych konwersja za pomocą `CUShort` funkcji; zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. Zobacz [przykład CInt](#cint-example) sekcji przykład.|  
  
 <sup>1</sup> ułamkowe mogą podlegać specjalny rodzaj zaokrąglania o nazwie *banker przez zaokrąglenie*. Aby uzyskać więcej informacji, zobacz "Uwagi".  
  
## <a name="remarks"></a>Uwagi  
 Zgodnie z zasadą, należy użyć funkcje konwersji typu języka Visual Basic mieszcząca metodach programu .NET Framework takiego jak `ToString()`, albo na <xref:System.Convert> klasy lub na poszczególnych typu struktury lub klasy. Funkcje języka Visual Basic są przeznaczone dla optymalnej interakcji z kodem języka Visual Basic, a także wprowadzić w kodzie źródłowym, krótsze i łatwiejsze do odczytania. Ponadto metody konwersji .NET Framework nie zawsze działają tak samo jak funkcje języka Visual Basic, na przykład podczas konwertowania `Boolean` do `Integer`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  

Począwszy od programu Visual Basic 15.8 floating-point na całkowite konwersji jest zoptymalizowane pod kątem podczas przekazywania <xref:System.Single> lub <xref:System.Double> wartość zwracana za pomocą następujących metod do jednej z funkcji konwersji liczby całkowitej (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Tego rodzaju optymalizacji umożliwia kod, który obsługuje dużą liczbę całkowitą konwersje można uruchomić maksymalnie na dwa razy szybciej. Poniższy przykład ilustruje te zoptymalizowane konwersje floating-point na całkowite:

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>Zachowanie  
  
-   **Wymuszenia.** Ogólnie rzecz biorąc można użyć funkcje konwersji typu danych można przekształcić wynik operacji do określonego typu danych, a nie domyślnym typem danych. Na przykład użyć `CDec` wymusić dziesiętna operacji arytmetycznych w przypadkach, w którym pojedynczej precyzji, podwójnej precyzji lub liczba całkowita arytmetyczne normalnie zajęłoby miejsce.  
  
-   **Konwersje nie powiodło się.** Jeśli `expression` przekazany do funkcji znajduje się poza zakresem typu danych, na który ma być przekonwertowany <xref:System.OverflowException> występuje.  
  
-   **Ułamkowe.** Podczas konwertowania nonintegral wartość całkowita, liczba całkowita funkcje konwersji typu (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, i `CUShort`) Usuń ułamkową część i zaokrąglania wartości do najbliższej liczby całkowitej.  
  
     Jeśli część ułamkową jest dokładnie 0,5, funkcje konwersji liczby całkowitej czytelności warto je zaokrąglić do najbliższej parzystej liczby całkowitej. Na przykład 0,5 zaokrągla 0, i w wersji 1.5 2.5, które zarówno zaokrąglanie do 2. Jest to czasem nazywane *banker przez zaokrąglenie*, a jej celem jest, aby zrekompensować odchylenie, który może gromadzenie podczas dodawania wielu takich liczb ze sobą.  
  
     `CInt` i `CLng` różnią się od <xref:Microsoft.VisualBasic.Conversion.Int%2A> i <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkcji, które truncate, zamiast zaokrąglanie część ułamkową liczby. Ponadto `Fix` i `Int` zawsze zwraca wartość typu danych, ponieważ są przekazywane w.  
  
-   **Data/Godzina konwersji.** Użyj <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkcję, aby określić, jeśli można przekonwertować wartości do daty i godziny. `CDate` rozpoznaje literałów dat i godzin, ale wartości liczbowe nie. Aby przekonwertować Visual Basic 6.0 `Date` wartość, która `Date` wartość w języku Visual Basic 2005 lub nowszych wersjach można użyć <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metody.  
  
-   **Niezależny od wartości daty/godziny.** [Date — typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md) zawsze zawiera informacje daty i godziny. W celu konwersji typu, Visual Basic traktuje 1/1/0001 (1 stycznia 1 rok) jako *neutralne wartość* dla daty i 00:00:00 (północ) jako neutralne wartość po raz. Po skonwertowaniu `Date` wartość na ciąg `CStr` nie zawiera neutralne wartości w ciągu wynikowym. Na przykład, jeśli można przekonwertować `#January 1, 0001 9:30:00#` na ciąg wyniku "9:30:00 AM"; informacje o dacie jest pomijane. Informacje o dacie jest jednak nadal znajdują się w oryginalnym `Date` wartości i można odzyskać za pomocą funkcji takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkcji.  
  
-   **Czułość kultury.** Funkcje konwersji typu obejmujące ciągi wykonać konwersje w oparciu o bieżące ustawienia kultury w aplikacji. Na przykład `CDate` rozpoznaje formaty daty zgodnie z ustawieniami regionalnymi systemu. Należy podać dzień, miesiąc i rok w odpowiedniej kolejności dla ustawień regionalnych lub datę nie może zostać zinterpretowane poprawnie. Nie rozpoznano formatu daty długiej, jeśli zawiera ciąg, dzień tygodnia, taki jak "Środa".  
  
     Jeśli musisz konwertować do lub z ciągu reprezentującego wartość w formacie innym niż ten, który został określony przez ustawienia regionalne, nie można użyć funkcje konwersji typu języka Visual Basic. Aby to zrobić, należy użyć `ToString(IFormatProvider)` i `Parse(String, IFormatProvider)` metod z typem tej wartości. Na przykład użyć <xref:System.Double.Parse%2A?displayProperty=nameWithType> podczas konwertowania ciągu do `Double`i użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na ciąg.  
  
## <a name="ctype-function"></a>CType — Funkcja  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md) przyjmuje drugi argument `typename`i przekształca wynik dane `expression` do `typename`, gdzie `typename` może być typu danych, struktury, klasy lub interfejsu, do której istnieje prawidłowa konwersja.  
  
 Porównanie `CType` przy użyciu innych typów słowa kluczowe konwersji, zobacz [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) i [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>Przykład CBool  
 W poniższym przykładzie użyto `CBool` funkcji konwersji wyrażenia do `Boolean` wartości. Jeśli wyrażenie ma wartość różną od zera, `CBool` zwraca `True`; w przeciwnym razie zwraca `False`.  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>Przykład CByte  
 W poniższym przykładzie użyto `CByte` funkcji konwersji wyrażenia `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>Przykład CChar  
 W poniższym przykładzie użyto `CChar` funkcję, aby skonwertować pierwszy znak `String` wyrażenie `Char` typu.  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 Argument wejściowy `CChar` musi być typu danych `Char` lub `String`. Nie można użyć `CChar` do konwertowania wartości na znak, ponieważ `CChar` nie może akceptować zawierającą dane typu liczbowego. Poniższy przykład pobiera liczba reprezentująca punkt kodowy (kod znaku) i konwertuje je do odpowiedniego znaku. Używa ona <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkcję, aby uzyskać ciąg cyfr, `CInt` konwersji ciągu znaków na typ `Integer`, i `ChrW` do przekonwertowania liczby na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>Przykład CDate  
 W poniższym przykładzie użyto `CDate` funkcji konwersji ciągów w celu `Date` wartości. Ogólnie rzecz biorąc kodować daty i godziny jako ciągi (jak pokazano w tym przykładzie) nie jest zalecane. Użyj literałów dat i godzin, takie jak #Feb 12, 1969 # i # 4:45:23 PM #, zamiast tego.  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>Przykład CDbl  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>Przykład CDec  
 W poniższym przykładzie użyto `CDec` funkcję, aby skonwertować wartość liczbowa `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>Przykład CInt  
 W poniższym przykładzie użyto `CInt` funkcję, aby przekonwertować wartości na `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>Przykład CLng
 W poniższym przykładzie użyto `CLng` funkcji konwersji wartości `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>Przykład CObj  
 W poniższym przykładzie użyto `CObj` funkcję, aby skonwertować wartość liczbowa `Object`. `Object` Sama zmienna zawierają tylko wskaźnik 4 bajtowych, które wskazuje `Double` wartości przypisanej do niego.  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>Przykład CSByte  
 W poniższym przykładzie użyto `CSByte` funkcję, aby skonwertować wartość liczbowa `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>Przykład CShort  
 W poniższym przykładzie użyto `CShort` funkcję, aby skonwertować wartość liczbowa `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>Przykład CSng  
 W poniższym przykładzie użyto `CSng` funkcji konwersji wartości `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>Przykład CStr  
 W poniższym przykładzie użyto `CStr` funkcję, aby skonwertować wartość liczbowa `String`.  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 W poniższym przykładzie użyto `CStr` funkcję, aby skonwertować `Date` wartości `String` wartości.  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` zawsze renderuje `Date` wartość w standardowym formacie krótkich dla bieżących ustawień regionalnych, na przykład, "6/15/2003 4:35:47 PM". Jednak `CStr` pomija *neutralne wartości* z 1/1/0001 dla daty i 00:00:00 czasu.  
  
 Aby uzyskać więcej szczegółów na wartości zwracane przez `CStr`, zobacz [zwrócić wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Przykład CUInt  
 W poniższym przykładzie użyto `CUInt` funkcję, aby skonwertować wartość liczbowa `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>Przykład CULng  
 W poniższym przykładzie użyto `CULng` funkcję, aby skonwertować wartość liczbowa `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>Przykład CUShort  
 W poniższym przykładzie użyto `CUShort` funkcję, aby skonwertować wartość liczbowa `UShort`.  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Funkcje konwersji](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Konwersje plików w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
