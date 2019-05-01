---
title: Typ danych — Podsumowanie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 29e5cbe09026dd52811c6c5fb88e940b45b7c0bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971746"
---
# <a name="data-type-summary-visual-basic"></a>Typ danych — Podsumowanie (Visual Basic)
W poniższej tabeli przedstawiono typy danych Visual Basic, ich obsługi popularnych typów środowiska wykonawczego dla języka, ich nominalnych alokacji i ich zakresami wartości.  
  
|Typ języka Visual Basic|Wspólna struktura typu środowiska uruchomieniowego języka|Nominalnych alokacji|Zakres wartości|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Zależy od implementacji platformy|`True` lub `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bajt|od 0 do 255 (bez znaku)|  
|[CHAR](../../../visual-basic/language-reference/data-types/char-data-type.md) (pojedynczy znak)|<xref:System.Char>|2 bajty|od 0 do 65535 (bez znaku)|  
|[Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bajtów|0:00:00 (północ), 1 stycznia 0001 do 11:59:59 PM 31 grudnia 9999 r|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bajtów|od 0 do +/-79,228,162,514,264,337,593,543,950,335 (+/-7,9... E + 28) <sup>†</sup> bez punktu dziesiętnego; od 0 do +/-7.9228162514264337593543950335 28 miejsc z prawej strony separatora dziesiętnego;<br /><br /> najmniejsza wartość różną od zera jest +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md) (podwójnej precyzji zmiennoprzecinkowego)|<xref:System.Double>|8 bajtów|-1.79769313486231570E + 308 do - 4.94065645841246544E-324 <sup>†</sup> dla wartości ujemnych;<br /><br /> 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 <sup>†</sup> dla wartości dodatnich|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bajty|-2,147,483,648 do 2 147 483 647 (z podpisem)|  
|[Długi](../../../visual-basic/language-reference/data-types/long-data-type.md) (liczba całkowita typu long)|<xref:System.Int64>|8 bajtów|-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807 (9.2... E + 18 <sup>†</sup>) (z podpisem)|  
|[Obiekt](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> (klasa)|4 bajty na platformie 32-bitowej<br /><br /> 8 bajtów na platformie 64-bitowej|Dowolny typ mogą być przechowywane w zmiennej typu `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bajt|od -128 do 127 (z podpisem)|  
|[Krótki](../../../visual-basic/language-reference/data-types/short-data-type.md) (krótka liczba całkowita)|<xref:System.Int16>|2 bajty|-32 768 za pośrednictwem 32 767 znaków (z podpisem)|  
|[Pojedynczy](../../../visual-basic/language-reference/data-types/single-data-type.md) (pojedynczej precyzji zmiennoprzecinkowego)|<xref:System.Single>|4 bajty|-3.4028235E + 38-do - 1, 401298E-45 <sup>†</sup> dla wartości ujemnych;<br /><br /> 1, 401298E-45 za pośrednictwem 3.4028235E + 38 <sup>†</sup> dla wartości dodatnich|  
|[Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md) (zmiennej długości)|<xref:System.String> (klasa)|Zależy od implementacji platformy|0 na około 2 mld znaki Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bajty|od 0 do 4 294 967 295 (bez znaku)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bajtów|od 0 do 18,446,744,073,709,551,615 (1.8... E + 19 <sup>†</sup>) (bez znaku)|  
|[Zdefiniowane przez użytkownika](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (struktury)|(dziedziczy <xref:System.ValueType>)|Zależy od implementacji platformy|Każdy element członkowski struktury ma zakres określany przez jego typu danych i jest niezależna od zakresów innych członków|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bajty|od 0 do 65 535 (bez znaku)|  
  
 <sup>†</sup> w *notacji wykładniczej*, "E", który odwołuje się do potęgą liczby 10. Dlatego 3.56E + 2 oznacza 3.56 x 10<sup>2</sup> lub 356 i 3.56E-2 oznacza 3.56 / 10<sup>2</sup> lub 0.0356.  
  
> [!NOTE]
>  W przypadku ciągów, które zawierają tekst, użyj <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkcji konwersji z formatu tekstowego na inny.  
  
 Oprócz określenia typu danych w instrukcji deklaracji, możesz wymusić typ danych niektórych elementów programowania przy użyciu znaku typu. Zobacz [wpisz znaków](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Użycie pamięci  
 Kiedy Deklarujesz na typ danych podstawowych, nie jest bezpiecznie przyjąć założenie, że użycie pamięci jest taka sama jak jego nominalnych alokacji. Jest to spowodowane następujące kwestie:  
  
- **Przypisanie magazynu.** Środowisko uruchomieniowe języka wspólnego można przypisać pamięci masowej, na podstawie bieżącej właściwości platformy, na którym jest wykonywany aplikacji. Jeśli pamięć jest prawie pełna, jego może pakietu zadeklarowanych elementów tak blisko siebie jak to możliwe. W innych przypadkach go może być dostosowanie ich adresów pamięci do naturalnych ograniczeń sprzętowych w celu zoptymalizowania wydajności.  
  
- **Szerokość platformy.** Przypisanie magazynu na platformie 64-bitowej różni się od przypisania na platformie 32-bitowej.  
  
### <a name="composite-data-types"></a>Złożone typy danych  
 To samo odnosi się do każdego członka złożonego typu danych, takie jak struktury lub tablicy. Nie można polegać na po prostu zsumowanie nominalnych alokacji elementów członkowskich typu. Ponadto istnieją inne zagadnienia, takie jak następujące:  
  
- **Koszty.** Niektóre typy złożone mają wymagania dodatkowej pamięci. Na przykład tablica używa dodatkową pamięć, macierz, sama, a także dla każdego wymiaru. Na platformie 32-bitowy to obciążenie jest obecnie 12 bajtów plus 8 bajtów dla każdego wymiaru. Na platformie 64-bitowej podwaja się to wymaganie.  
  
- **Układ magazynu.** Nie można bezpiecznie przyjąć, że kolejność przechowywania w pamięci jest taka sama jak kolejność zgłoszenia. Jeszcze nie może wprowadzać założeń dotyczących bajtowe wyrównanie, takie jak 2-bajtowych i 4-bajtowych granic. Jeśli definiujesz klasy lub struktury, a należy kontrolować układ magazynu z jej członków, można zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu klasy lub struktury.  
  
### <a name="object-overhead"></a>Obciążenie obiektu  
 `Object` Odwołujące się do żadnych danych podstawowych lub złożonego typu używa 4 bajtów oprócz danych znajdujących się na typ danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
