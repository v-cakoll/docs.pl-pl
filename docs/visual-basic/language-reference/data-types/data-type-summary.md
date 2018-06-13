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
ms.openlocfilehash: 8afeba3f88c4bfe6e1c9777f950c3b458665e340
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591797"
---
# <a name="data-type-summary-visual-basic"></a>Typ danych — Podsumowanie (Visual Basic)
W poniższej tabeli przedstawiono typy danych Visual Basic, typy obsługi środowiska uruchomieniowego języka wspólnego ich Alokacja magazynu nominalnego i ich zakresów wartości.  
  
|Typ Visual Basic|Wspólna struktura typu środowiska uruchomieniowego języka|Alokacja magazynu nominalnego|Zakres wartości|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Zależy od implementacji platformy|`True` lub `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bajt|0 do 255 (bez znaku)|  
|[CHAR](../../../visual-basic/language-reference/data-types/char-data-type.md) (pojedynczy znak)|<xref:System.Char>|2 bajty|od 0 do 65535 (bez znaku)|  
|[Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bajtów|0:00:00 (północ) 1 stycznia 0001 do 11:59:59 PM 31 grudnia 9999 r|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bajtów|od 0 do +/-79,228,162,514,264,337,593,543,950,335 (+/-7,9... E + 28) <sup>†</sup> bez punktu dziesiętnego; 0 za pośrednictwem +/-7.9228162514264337593543950335 28 miejsc z prawej strony dziesiętnego;<br /><br /> najmniejszą liczbę różną od zera jest +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Podwójna](../../../visual-basic/language-reference/data-types/double-data-type.md) (podwójnej precyzji zmiennoprzecinkowe)|<xref:System.Double>|8 bajtów|-1.79769313486231570E + 308 do - 4.94065645841246544E-324 <sup>†</sup> dla wartości ujemnych;<br /><br /> 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 <sup>†</sup> dla wartości dodatnie|  
|[Liczba całkowita](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bajty|-2,147,483,648 do 2 147 483 647 (ze znakiem)|  
|[Długie](../../../visual-basic/language-reference/data-types/long-data-type.md) (długich liczb całkowitych)|<xref:System.Int64>|8 bajtów|-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807 (9.2... E + 18 <sup>†</sup>) (ze znakiem)|  
|[Obiekt](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> (klasa)|4 bajty na platformie 32-bitowych<br /><br /> 8 bajtów na 64-bitowej platformy|Dowolnego typu mogą być przechowywane w zmiennej typu `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bajt|-128 do 127 znaków (ze znakiem)|  
|[Krótki](../../../visual-basic/language-reference/data-types/short-data-type.md) (krótka liczba całkowita)|<xref:System.Int16>|2 bajty|-32 768 do 32 767 (ze znakiem)|  
|[Pojedynczy](../../../visual-basic/language-reference/data-types/single-data-type.md) (pojedynczej precyzji zmiennoprzecinkowe)|<xref:System.Single>|4 bajty|-3.4028235E + 38 do - 1, 401298E-45 <sup>†</sup> dla wartości ujemnych;<br /><br /> 1, 401298E-45 za pośrednictwem 3.4028235E + 38 <sup>†</sup> dla wartości dodatnie|  
|[Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md) (zmiennej długości)|<xref:System.String> (klasa)|Zależy od implementacji platformy|0, aby około 2 miliardów znaków Unicode|  
|[Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bajty|od 0 do 4 294 967 295 (bez znaku)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bajtów|od 0 do 18,446,744,073,709,551,615 (1.8... E + 19 <sup>†</sup>) (bez znaku)|  
|[Zdefiniowane przez użytkownika](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (struktury)|(dziedziczy <xref:System.ValueType>)|Zależy od implementacji platformy|Każdy element członkowski struktury ma zakres określony przez jego typu danych i niezależnie od innych członków określonych zakresów|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bajty|od 0 do 65 535 (bez znaku)|  
  
 <sup>†</sup> w *notacji naukowej*, "E" odwołuje się do potęgi liczby 10. Dlatego 3.56E + 2 oznacza 3.56 x 10<sup>2</sup> lub 356 i 3.56E-2 oznacza 3.56 / 10<sup>2</sup> lub 0.0356.  
  
> [!NOTE]
>  Ciągi zawierające tekst, użyj <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkcji konwersji z formatu tekstowego na inny.  
  
 Oprócz określenia typu danych w instrukcji deklaracji, możesz wymusić typu danych niektóre elementy programowania przy użyciu znaku typu. Zobacz [wpisz znaki](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Zużycie pamięci  
 W deklaracji z typem danych podstawowych, nie jest bezpieczne zakładać, że użycie pamięci jest taki sam jak jej alokacja nominalnego magazynu. Jest to spowodowane następujące kwestie:  
  
-   **Przypisanie magazynu.** Środowisko uruchomieniowe języka wspólnego można przypisać magazynu na podstawie bieżącego charakterystyk platformy, na którym jest wykonywany aplikacji. Jeśli ilość pamięci jest prawie pełna, zadeklarowanych elementów jako ściśle go może pakietu ze sobą, jak to możliwe. W innych przypadkach może ona zgodna ich adresów pamięci do granicy fizyczne sprzętu w celu zoptymalizowania wydajności.  
  
-   **Szerokość platformy.** Przypisanie magazynu na 64-bitowej platformy różni się od przypisania na platformie 32-bitowych.  
  
### <a name="composite-data-types"></a>Złożone typy danych  
 Te same kwestie do każdego elementu członkowskiego typu danych, na przykład struktury lub tablicy. Nie może zależeć po prostu zsumowanie alokacji magazynu nominalnego elementów członkowskich typu. Ponadto istnieją inne względy, takie jak następujące:  
  
-   **Koszty.** Niektóre typy złożone mają wymagania dotyczące więcej pamięci. Na przykład tablicy używa dodatkową pamięć dla tablicy samej siebie, a także dla każdego wymiaru. Na platformie 32-bitowy to obciążenie jest obecnie 12 bajtów plus 8 bajtów dla każdego wymiaru. W 64-bitowej platformy to wymaganie jest podwójny.  
  
-   **Układ magazynu.** Nie można bezpiecznie zakładać, że kolejność magazynu w pamięci jest taka sama jak zamówienia deklaracji. Nie można wprowadzić nawet założenia dotyczące wyrównanie bajt, takich jak granic 2-bajtowych lub 4-bajtowych. Jeśli definiujesz klasy lub struktury i należy kontrolować układ magazynu jego elementów członkowskich, można zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu klasy lub struktury.  
  
### <a name="object-overhead"></a>Narzut obiektu  
 `Object` Odwołujących się do żadnych danych podstawowych lub złożonego typu używa 4 bajty oprócz danych znajdujących się na typ danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
