---
title: Funkcje konwersji typu
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
ms.openlocfilehash: 5c0cfae01da02222d0827e81ec1ed35ce353ead1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415378"
---
# <a name="type-conversion-functions-visual-basic"></a>Funkcje konwersji typu (Visual Basic)

Te funkcje są kompilowane w tekście, co oznacza, że kod konwersji jest częścią kodu, który szacuje wyrażenie. Czasami nie istnieje wywołanie procedury w celu wykonania konwersji, co zwiększa wydajność. Każda funkcja przekształca wyrażenie na określony typ danych.

## <a name="syntax"></a>Składnia

```vb
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
Wymagany. Dowolne wyrażenie typu danych źródłowych.

## <a name="return-value-data-type"></a>Typ danych wartości zwracanej

Nazwa funkcji określa typ danych zwracanej wartości, jak pokazano w poniższej tabeli.

|Nazwa funkcji|Zwraca typ danych|Zakres dla `expression` argumentu|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[Boolean, typ danych](../data-types/boolean-data-type.md)|Dowolne prawidłowe `Char` lub `String` liczbowe wyrażenie.|
|`CByte`|[Byte, typ danych](../data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType>(0) do <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaku); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na liczbę bajtów z `CByte` funkcją; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|
|`CChar`|[Char, typ danych](../data-types/char-data-type.md)|Wszystkie prawidłowe `Char` lub `String` wyrażenie; tylko pierwszy znak `String` jest konwertowany; wartość może być od 0 do 65535 (bez znaku).|
|`CDate`|[Date, typ danych](../data-types/date-data-type.md)|Dowolna prawidłowa reprezentacja daty i godziny.|
|`CDbl`|[Double, typ danych](../data-types/double-data-type.md)|-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 dla wartości ujemnych; 4.94065645841246544 e-324 za pośrednictwem 1.79769313486231570 E + 308 dla wartości dodatnich.|
|`CDec`|[Decimal, typ danych](../data-types/decimal-data-type.md)|+/-79228162514264337593543950335 dla liczb o zerowej skali, czyli liczb bez miejsc dziesiętnych. W przypadku liczb z 28 miejscami dziesiętnymi zakresem jest +/-7.9228162514264337593543950335. Najmniejsza możliwa liczba różna od zera to 0,0000000000000000000000000001 (+/-1E-28).|
|`CInt`|[Integer, typ danych](../data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType>(-2 147 483 648) do <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); części ułamkowe są zaokrąglane.<sup> 1</sup> <br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na liczbę całkowitą przy użyciu `CInt` funkcji; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) . |
|`CLng`|[Long, typ danych](../data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType>(-zakresu od) do <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność operacji zmiennoprzecinkowych do 64-bitowej konwersji liczb całkowitych za pomocą `CLng` funkcji; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|
|`CObj`|[Object — typ danych](../data-types/object-data-type.md)|Dowolne prawidłowe wyrażenie.|
|`CSByte`|[SByte, typ danych](../data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType>(-128) do <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność przeprowadzenia zmiennoprzecinkowej konwersji bajtów z `CSByte` funkcją; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|
|`CShort`|[Short, typ danych](../data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType>(-32 768) do <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na 16-bitową liczbę całkowitą z `CShort` funkcją; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|
|`CSng`|[Single, typ danych](../data-types/single-data-type.md)|-3.402823 e + 38 do-1.401298 E-45 dla wartości ujemnych; 1.401298 e-45 za pośrednictwem 3.402823 E + 38 w przypadku wartości dodatnich.|
|`CStr`|[Typ danych ciągu](../data-types/string-data-type.md)|Zwraca wartość, która jest `CStr` zależna od `expression` argumentu. Zobacz [wartości zwracane dla funkcji CStr](return-values-for-the-cstr-function.md).|
|`CUInt`|[UInteger, typ danych](../data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType>(0) do <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaku); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej do niepodpisanej liczby całkowitej z `CUInt` funkcją; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|
|`CULng`|[ULong, typ danych](../data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType>(0) do <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615 są) (bez znaku); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność operacji zmiennoprzecinkowych do konwersji długich liczb całkowitych bez znaku przy użyciu `CULng` funkcji; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|
|`CUShort`|[UShort, typ danych](../data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType>(0) do <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaku); części ułamkowe są zaokrąglane.<sup> 1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność zmiennoprzecinkowej niepodpisanej 16-bitowej konwersji liczb całkowitych za pomocą `CUShort` funkcji; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|

<sup>1</sup> części ułamkowe mogą podlegać specjalnemu typowi zaokrąglania wywołanemu przez *Bank*. Aby uzyskać więcej informacji, zobacz "uwagi".

## <a name="remarks"></a>Uwagi

Jako regułę należy użyć funkcji konwersji typu Visual Basic w preferencjach do metod .NET Framework, takich jak `ToString()` , na <xref:System.Convert> klasie lub w poszczególnych typach lub klasach. Funkcje Visual Basic są przeznaczone do optymalnej interakcji z kodem Visual Basic, a także sprawiają, że kod źródłowy jest krótszy i łatwiejszy do odczytania. Ponadto metody konwersji .NET Framework nie zawsze generują te same wyniki, co w przypadku funkcji Visual Basic, na przykład podczas konwertowania `Boolean` na `Integer` . Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

Począwszy od Visual Basic 15,8, wydajność konwersji zmiennoprzecinkowej na liczbę całkowitą jest zoptymalizowana, gdy przekażesz <xref:System.Single> lub <xref:System.Double> wartość zwrócona przez następujące metody do jednej z funkcji konwersji liczb całkowitych (,,,,,,, `CByte` `CShort` `CInt` `CLng` `CSByte` `CUShort` `CUInt` `CULng` ):

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

Ta optymalizacja umożliwia kod, który wykonuje dużą liczbę konwersji liczb całkowitych do dwukrotnego uruchamiania. Poniższy przykład ilustruje te zoptymalizowane konwersje zmiennoprzecinkowe do liczby całkowitej:

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

- **Wymuszanie.** Ogólnie rzecz biorąc, można użyć funkcji konwersji typu danych, aby przekształcić wynik operacji do określonego typu danych, a nie domyślnego typu danych. Na przykład, można użyć, `CDec` Aby wymusić arytmetyczne wartości dziesiętne w przypadkach, gdy zwykle odbywa się arytmetyczne pojedynczej precyzji o podwójnej precyzji lub liczbie całkowitej.

- **Konwersje zakończone niepowodzeniem.** Jeśli `expression` przekazanie do funkcji znajduje się poza zakresem typu danych, do którego ma zostać przekonwertowane, <xref:System.OverflowException> występuje.

- **Części ułamkowe.** W przypadku konwersji niecałkowitej wartości na typ całkowity funkcja konwersji liczb całkowitych (,,,,,, `CByte` `CInt` `CLng` `CSByte` `CShort` `CUInt` `CULng` i `CUShort` ) Usuń część ułamkową i Zaokrąglij wartość do najbliższej liczby całkowitej.

     Jeśli część ułamkowa ma wartość dokładnie 0,5, funkcja konwersji liczb całkowitych zaokrągli ją do najbliższej parzystej liczby całkowitej. Na przykład 0,5 zaokrągla do 0, i 1,5 i 2,5 oba do 2. Jest to czasami nazywane *zaokrąglaniem w banku*, a jego celem jest zrekompensowanie odchylenia, które może wystąpić w przypadku dodawania wielu takich liczb jednocześnie.

     `CInt`i `CLng` różnią się <xref:Microsoft.VisualBasic.Conversion.Int%2A> od <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkcji i, które obcinają część ułamkową liczby. Ponadto, `Fix` i `Int` zawsze zwracają wartość tego samego typu danych, które są przekazywane.

- **Konwersje daty/godziny.** Użyj <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkcji, aby określić, czy wartość może zostać przekonwertowana na datę i godzinę. `CDate`rozpoznaje literały daty i literały czasowe, ale nie wartości numeryczne. Aby przekonwertować wartość Visual Basic 6,0 `Date` na `Date` wartość w Visual Basic 2005 lub nowszej wersji, można użyć <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metody.

- **Neutralne wartości daty/godziny.** [Typ danych Data](../data-types/date-data-type.md) zawsze zawiera informacje o dacie i godzinie. Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu. W przypadku konwersji `Date` wartości na ciąg, nie `CStr` zawiera neutralnych wartości w ciągu będącym wynikiem. Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 am"; informacje o dacie są pomijane. Jednak informacje o dacie są nadal obecne w pierwotnej `Date` wartości i mogą być odzyskiwane za pomocą funkcji, takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Funkcja.

- **Czułość kultury.** Funkcje konwersji typów obejmujące ciągi wykonują konwersje w oparciu o bieżące ustawienia kultury dla aplikacji. Na przykład program `CDate` rozpoznaje formaty dat zgodnie z ustawieniami regionalnymi systemu. Musisz podać dzień, miesiąc i rok w prawidłowej kolejności dla ustawień regionalnych lub Data może nie być interpretowana poprawnie. Format daty długiej nie jest rozpoznawany, jeśli zawiera ciąg dni tygodnia, taki jak "Środa".

     Jeśli konieczne jest przekonwertowanie na lub z ciągu reprezentującego wartość w formacie innym niż określony przez ustawienia regionalne, nie można użyć funkcji konwersji typu Visual Basic. W tym celu należy użyć `ToString(IFormatProvider)` metod i `Parse(String, IFormatProvider)` typu tej wartości. Na przykład, użyć <xref:System.Double.Parse%2A?displayProperty=nameWithType> podczas konwertowania ciągu na a `Double` i użyć <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na ciąg.

## <a name="ctype-function"></a>CType — Funkcja

[Funkcja CType](ctype-function.md) przyjmuje drugi argument, `typename` , i przekształcenie `expression` na `typename` , gdzie `typename` może być dowolnego typu danych, struktury, klasy lub interfejsu, do którego istnieje prawidłowa konwersja.

Aby porównać z `CType` innymi słowami kluczowymi konwersji, zobacz [operator DirectCast](../operators/directcast-operator.md) i [operator TryCast](../operators/trycast-operator.md).

## <a name="cbool-example"></a>Przykład CBool

Poniższy przykład używa funkcji, `CBool` Aby przekonwertować wyrażenia na `Boolean` wartości. Jeśli wyrażenie daje w wyniku wartość różną od zera, `CBool` zwraca `True` ; w przeciwnym razie zwraca wartość `False` .

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a>Przykład CByte

Poniższy przykład używa funkcji, `CByte` Aby przekonwertować wyrażenie na `Byte` .

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a>Przykład CChar

Poniższy przykład używa funkcji, `CChar` Aby skonwertować pierwszy znak `String` wyrażenia na `Char` Typ.

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

Argument wejściowy `CChar` musi być typu danych `Char` lub `String` . Nie można użyć `CChar` do konwersji liczby na znak, ponieważ `CChar` nie można zaakceptować typu danych liczbowych. Poniższy przykład pobiera liczbę reprezentującą punkt kodu (kod znaku) i konwertuje ją na odpowiedni znak. Używa <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkcji w celu uzyskania ciągu cyfr, `CInt` przekonwertowania ciągu na typ `Integer` i `ChrW` przekonwertowania liczby na typ `Char` .

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a>Przykład CDate

Poniższy przykład używa funkcji, `CDate` Aby przekonwertować ciągi na `Date` wartości. Ogólnie rzecz biorąc, stałe kodowanie i godziny w postaci ciągów (jak pokazano w tym przykładzie) nie są zalecane. Używaj literałów daty i literałów czasowych, takich jak #Feb 12, 1969 # i #4:45:23 PM #, zamiast.

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a>Przykład CDbl

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a>Przykład CDec

Poniższy przykład używa funkcji, `CDec` Aby przekonwertować wartość liczbową na `Decimal` .

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a>Przykład CInt

Poniższy przykład używa funkcji, `CInt` Aby przekonwertować wartość na `Integer` .

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a>Przykład CLng

Poniższy przykład używa funkcji, `CLng` Aby przekonwertować wartości na `Long` .

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a>Przykład CObj

Poniższy przykład używa funkcji, `CObj` Aby przekonwertować wartość liczbową na `Object` . `Object`Sama zmienna zawiera tylko wskaźnik z czterema bajtami, który wskazuje na `Double` przypisaną do niej wartość.

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a>Przykład CSByte

Poniższy przykład używa funkcji, `CSByte` Aby przekonwertować wartość liczbową na `SByte` .

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a>Przykład CShort

Poniższy przykład używa funkcji, `CShort` Aby przekonwertować wartość liczbową na `Short` .

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a>Przykład CSng

Poniższy przykład używa funkcji, `CSng` Aby przekonwertować wartości na `Single` .

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a>Przykład CStr

Poniższy przykład używa funkcji, `CStr` Aby przekonwertować wartość liczbową na `String` .

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

Poniższy przykład używa funkcji, `CStr` Aby przekonwertować `Date` wartości na `String` wartości.

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

`CStr`zawsze renderuje `Date` wartość w standardowym formacie, na przykład "6/15/2003 4:35:47 PM". Jednakże `CStr` pomija *wartości neutralnych* 1/1/0001 dla daty i 00:00:00 przez czas.

Aby uzyskać więcej szczegółów na temat wartości zwracanych przez `CStr` , zobacz [zwracają wartości dla funkcji CStr](return-values-for-the-cstr-function.md).

## <a name="cuint-example"></a>Przykład CUInt

Poniższy przykład używa funkcji, `CUInt` Aby przekonwertować wartość liczbową na `UInteger` .

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a>Przykład CULng

Poniższy przykład używa funkcji, `CULng` Aby przekonwertować wartość liczbową na `ULong` .

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a>Przykład CUShort

Poniższy przykład używa funkcji, `CUShort` Aby przekonwertować wartość liczbową na `UShort` .

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a>Zobacz też

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
- [Funkcje konwersji](conversion-functions.md)
- [Konwersje plików w Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
