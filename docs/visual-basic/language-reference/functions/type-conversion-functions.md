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
ms.openlocfilehash: 6b448fa23368f7a0848c44362337b0ccc70b6162
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592074"
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
  
## <a name="part"></a>Części  
 `expression`  
 Wymagany. Dowolne wyrażenie typu danych źródłowych.  
  
## <a name="return-value-data-type"></a>Typ danych wartości zwracanej  
 Nazwa funkcji określa typ danych zwracanej wartości, jak pokazano w poniższej tabeli.  
  
|Nazwa funkcji|Zwraca typ danych|Zakres dla `expression` argumentu|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Dowolny prawidłowy `Char` lub `String` lub wyrażenie liczbowe.|  
|`CByte`|[Byte, typ danych](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) do <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na liczbę bajtów za pomocą funkcji `CByte`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
|`CChar`|[Char, typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)|Dowolne prawidłowe wyrażenie `Char` lub `String`; konwertowany jest tylko pierwszy znak `String`; wartość może być równa 0 – 65535 (bez znaku).|  
|`CDate`|[Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Dowolna prawidłowa reprezentacja daty i godziny.|  
|`CDbl`|[Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 dla wartości ujemnych; 4.94065645841246544 e-324 za pośrednictwem 1.79769313486231570 E + 308 dla wartości dodatnich.|  
|`CDec`|[Decimal, typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79228162514264337593543950335 dla liczb o zerowej skali, czyli liczb bez miejsc dziesiętnych. W przypadku liczb z 28 miejscami dziesiętnymi zakresem jest +/-7.9228162514264337593543950335. Najmniejsza możliwa liczba różna od zera to 0,0000000000000000000000000001 (+/-1E-28).|  
|`CInt`|[Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2 147 483 648) do <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); części ułamkowe są zaokrąglane. <sup>1</sup> <br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na liczbę całkowitą przy użyciu funkcji `CInt`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) . |  
|`CLng`|[Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-zakresu od) do <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność liczby zmiennoprzecinkowej do 64-bitowej konwersji liczb całkowitych za pomocą funkcji `CLng`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
|`CObj`|[Object, typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md)|Dowolne prawidłowe wyrażenie.|  
|`CSByte`|[SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) do <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność przeprowadzenia zmiennoprzecinkowej konwersji bajtów z funkcją `CSByte`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
|`CShort`|[Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) do <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej na 16-bitową liczbę całkowitą przy użyciu funkcji `CShort`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
|`CSng`|[Single, typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 do-1.401298 E-45 dla wartości ujemnych; 1.401298 e-45 za pośrednictwem 3.402823 E + 38 w przypadku wartości dodatnich.|  
|`CStr`|[String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)|Funkcja zwraca dla `CStr` zależy od argumentu `expression`. Zobacz [wartości zwracane dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) do <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność konwersji zmiennoprzecinkowej do niepodpisanej liczby całkowitej przy użyciu funkcji `CUInt`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
|`CULng`|[ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) do <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615 są) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność operacji zmiennoprzecinkowych do konwersji długich liczb całkowitych bez znaku przy użyciu funkcji `CULng`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
|`CUShort`|[UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) do <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaku); części ułamkowe są zaokrąglane. <sup>1</sup><br/><br/>Począwszy od Visual Basic 15,8, Visual Basic optymalizuje wydajność zmiennoprzecinkowej niepodpisanej 16-bitowej konwersji liczb całkowitych za pomocą funkcji `CUShort`; Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. Zapoznaj się z przykładową sekcją [przykładu CInt](#cint-example) .|  
  
 <sup>1</sup> części ułamkowe mogą podlegać specjalnemu typowi zaokrąglania wywołanemu przez *Bank*. Aby uzyskać więcej informacji, zobacz "uwagi".  
  
## <a name="remarks"></a>Uwagi  
 Jako regułę należy użyć funkcji konwersji typu Visual Basic w preferencjach do metod .NET Framework, takich jak `ToString()`, w klasie <xref:System.Convert> lub w strukturze lub klasie poszczególnych typów. Funkcje Visual Basic są przeznaczone do optymalnej interakcji z kodem Visual Basic, a także sprawiają, że kod źródłowy jest krótszy i łatwiejszy do odczytania. Ponadto metody konwersji .NET Framework nie zawsze generują te same wyniki co funkcje Visual Basic, na przykład podczas konwertowania `Boolean` na `Integer`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  

Począwszy od Visual Basic 15,8, wydajność konwersji zmiennoprzecinkowej na liczbę całkowitą jest zoptymalizowana w przypadku przekazania wartości <xref:System.Single> lub <xref:System.Double> zwróconej przez następujące metody do jednej z funkcji konwersji liczb całkowitych (`CByte`, `CShort`, `CInt`, @no__ t-5, `CSByte`, `CUShort`, `CUInt`, `CULng`):

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
  
- **Wymuszanie.** Ogólnie rzecz biorąc, można użyć funkcji konwersji typu danych, aby przekształcić wynik operacji do określonego typu danych, a nie domyślnego typu danych. Na przykład użyj `CDec`, aby wymusić arytmetyczną liczbę dziesiętną w przypadkach, gdy zwykle odbywa się przeprowadzenie arytmetycznej pojedynczej precyzji, podwójnej precyzji lub liczby całkowitej.  
  
- **Konwersje zakończone niepowodzeniem.** Jeśli wartość `expression` przeniesiona do funkcji znajduje się poza zakresem typu danych, do którego ma zostać przekonwertowane, występuje <xref:System.OverflowException>.  
  
- **Części ułamkowe.** W przypadku konwersji niecałkowitej wartości na typ całkowity funkcje konwersji liczb całkowitych (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` i `CUShort`) Usuń część ułamkową i Zaokrąglij wartość do najbliższej liczby całkowitej.  
  
     Jeśli część ułamkowa ma wartość dokładnie 0,5, funkcja konwersji liczb całkowitych zaokrągli ją do najbliższej parzystej liczby całkowitej. Na przykład 0,5 zaokrągla do 0, i 1,5 i 2,5 oba do 2. Jest to czasami nazywane *zaokrąglaniem w banku*, a jego celem jest zrekompensowanie odchylenia, które może wystąpić w przypadku dodawania wielu takich liczb jednocześnie.  
  
     `CInt` i `CLng` różnią się od funkcji <xref:Microsoft.VisualBasic.Conversion.Int%2A> i <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, które obcinają część ułamkową liczby. Ponadto `Fix` i `Int` zawsze zwracają wartość tego samego typu danych co przekazane.  
  
- **Konwersje daty/godziny.** Użyj funkcji <xref:Microsoft.VisualBasic.Information.IsDate%2A>, aby określić, czy wartość może zostać przekonwertowana na datę i godzinę. `CDate` rozpoznaje literały daty i literały czasowe, ale nie wartości numeryczne. Aby przekonwertować wartość Visual Basic 6,0 `Date` na wartość `Date` w Visual Basic 2005 lub nowszych wersjach, można użyć metody <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.  
  
- **Neutralne wartości daty/godziny.** [Typ danych Data](../../../visual-basic/language-reference/data-types/date-data-type.md) zawsze zawiera informacje o dacie i godzinie. Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu. W przypadku konwersji wartości `Date` na ciąg, `CStr` nie zawiera neutralnych wartości w ciągu będącym wynikiem. Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 AM"; Informacje o dacie są pomijane. Jednakże informacje o dacie są nadal obecne w oryginalnej wartości `Date` i mogą być odzyskiwane za pomocą funkcji, takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkcja.  
  
- **Czułość kultury.** Funkcje konwersji typów obejmujące ciągi wykonują konwersje w oparciu o bieżące ustawienia kultury dla aplikacji. Na przykład `CDate` rozpoznaje formaty dat zgodnie z ustawieniami regionalnymi systemu. Musisz podać dzień, miesiąc i rok w prawidłowej kolejności dla ustawień regionalnych lub Data może nie być interpretowana poprawnie. Format daty długiej nie jest rozpoznawany, jeśli zawiera ciąg dni tygodnia, taki jak "Środa".  
  
     Jeśli konieczne jest przekonwertowanie na lub z ciągu reprezentującego wartość w formacie innym niż określony przez ustawienia regionalne, nie można użyć funkcji konwersji typu Visual Basic. W tym celu należy użyć metod `ToString(IFormatProvider)` i `Parse(String, IFormatProvider)` typu tej wartości. Na przykład użyj <xref:System.Double.Parse%2A?displayProperty=nameWithType> podczas konwertowania ciągu na `Double` i użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na ciąg.  
  
## <a name="ctype-function"></a>CType — Funkcja  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md) przyjmuje drugi argument, `typename` i przekształcenie `expression` do `typename`, gdzie `typename` może być dowolnym typem danych, strukturą, klasą lub interfejsem, do którego istnieje prawidłowa konwersja.  
  
 Aby porównać `CType` z innymi słowami kluczowymi konwersji, zobacz [operator DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) i [operator TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>Przykład CBool  
 W poniższym przykładzie zastosowano funkcję `CBool` w celu przekonwertowania wyrażeń na wartości `Boolean`. Jeśli wyrażenie daje w wyniku wartość różną od zera, `CBool` zwraca `True`; w przeciwnym razie zwraca `False`.  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>Przykład CByte  
 W poniższym przykładzie zastosowano funkcję `CByte`, aby przekonwertować wyrażenie na `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>Przykład CChar  
 W poniższym przykładzie zastosowano funkcję `CChar` w celu przekonwertowania pierwszego znaku wyrażenia `String` na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 Argument wejściowy do `CChar` musi być typu danych `Char` lub `String`. Nie można użyć `CChar` do przekonwertowania liczby na znak, ponieważ `CChar` nie może akceptować typu danych liczbowych. Poniższy przykład pobiera liczbę reprezentującą punkt kodu (kod znaku) i konwertuje ją na odpowiedni znak. Używa funkcji <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> w celu uzyskania ciągu cyfr, `CInt` do przekonwertowania ciągu na typ `Integer` i `ChrW`, aby przekonwertować liczbę na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>Przykład CDate  
 W poniższym przykładzie zastosowano funkcję `CDate` w celu przekonwertowania ciągów na wartości `Date`. Ogólnie rzecz biorąc, stałe kodowanie i godziny w postaci ciągów (jak pokazano w tym przykładzie) nie są zalecane. Używaj literałów daty i literałów czasowych, takich jak #Feb 12, 1969 # i #4:45:23 PM #, zamiast.  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>Przykład CDbl  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>Przykład CDec  
 W poniższym przykładzie zastosowano funkcję `CDec` w celu przekonwertowania wartości liczbowej na `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>Przykład CInt  
 W poniższym przykładzie zastosowano funkcję `CInt` w celu przekonwertowania wartości na `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>Przykład CLng
 W poniższym przykładzie zastosowano funkcję `CLng` w celu przekonwertowania wartości na `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>Przykład CObj  
 W poniższym przykładzie zastosowano funkcję `CObj` w celu przekonwertowania wartości liczbowej na `Object`. Sama zmienna `Object` zawiera tylko dwubajtowy wskaźnik wskazujący na przypisaną wartość `Double`.  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>Przykład CSByte  
 W poniższym przykładzie zastosowano funkcję `CSByte` w celu przekonwertowania wartości liczbowej na `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>Przykład CShort  
 W poniższym przykładzie zastosowano funkcję `CShort` w celu przekonwertowania wartości liczbowej na `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>Przykład CSng  
 W poniższym przykładzie zastosowano funkcję `CSng` w celu przekonwertowania wartości na `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>Przykład CStr  
 W poniższym przykładzie zastosowano funkcję `CStr` w celu przekonwertowania wartości liczbowej na `String`.  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 W poniższym przykładzie zastosowano funkcję `CStr` w celu przekonwertowania wartości `Date` na wartości `String`.  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` zawsze renderuje wartość `Date` w standardowym krótkim formacie dla bieżących ustawień regionalnych, na przykład "6/15/2003 4:35:47 PM". Jednak `CStr` pomija *wartości neutralnych* 1/1/0001 dla daty i 00:00:00 przez czas.  
  
 Aby uzyskać więcej szczegółów na temat wartości zwracanych przez `CStr`, zobacz [zwracają wartości dla funkcji CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Przykład CUInt  
 W poniższym przykładzie zastosowano funkcję `CUInt` w celu przekonwertowania wartości liczbowej na `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>Przykład CULng  
 W poniższym przykładzie zastosowano funkcję `CULng` w celu przekonwertowania wartości liczbowej na `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>Przykład CUShort  
 W poniższym przykładzie zastosowano funkcję `CUShort` w celu przekonwertowania wartości liczbowej na `UShort`.  
  
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
- [Konwersje typów w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
