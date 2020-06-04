---
title: Typy danych — podsumowanie
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
ms.openlocfilehash: 5eb52ef937a677c0b7498d058b5a39a375351ddc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415624"
---
# <a name="data-type-summary-visual-basic"></a>Typ danych — Podsumowanie (Visual Basic)

W poniższej tabeli przedstawiono typy danych Visual Basic, ich obsługę typów środowiska uruchomieniowego języka wspólnego, ich nominalna alokacja magazynu oraz ich zakresów wartości.  
  
|Typ Visual Basic|Struktura typów środowiska uruchomieniowego języka wspólnego|Nominalna alokacja magazynu|Zakres wartości|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Wartość logiczna](boolean-data-type.md)|<xref:System.Boolean>|Zależy od implementacji platformy|`True` lub `False`|  
|[Bajc](byte-data-type.md)|<xref:System.Byte>|1 bajt|od 0 do 255 (bez znaku)|  
|[Char](char-data-type.md) (pojedynczy znak)|<xref:System.Char>|2 bajty|od 0 do 65535 (bez znaku)|  
|[Date](date-data-type.md)|<xref:System.DateTime>|8 bajtów|0:00:00 (północ) 1 stycznia 0001 do 11:59:59 PM w dniu 31 grudnia 9999|  
|[Dokładności](decimal-data-type.md)|<xref:System.Decimal>|16 bajtów|od 0 do +/-79228162514264337593543950335 (+/-7.9...E + 28) <sup>†</sup> bez punktu dziesiętnego; od 0 do +/-7.9228162514264337593543950335 z 28 miejscami po prawej stronie wartości dziesiętnej;<br /><br /> najmniejsza liczba różna od zera to +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Double](double-data-type.md) (zmiennoprzecinkowe o podwójnej precyzji)|<xref:System.Double>|8 bajtów|-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 <sup>†</sup> dla wartości ujemnych;<br /><br /> 4.94065645841246544 e-324 za pośrednictwem 1.79769313486231570 E + 308 <sup>†</sup> dla wartości dodatnich|  
|[Liczba całkowita](integer-data-type.md)|<xref:System.Int32>|4 bajty|-2 147 483 648 do 2 147 483 647 (podpisane)|  
|[Long](long-data-type.md) (Long Integer)|<xref:System.Int64>|8 bajtów|-zakresu od do 9 223 372 036 854 775 807 (9.2... E + 18 <sup>†</sup>) (podpisane)|  
|[Obiekt](object-data-type.md)|<xref:System.Object>określonej|4 bajty na 32-bitowej platformie<br /><br /> 8 bajtów na 64-bitowej platformie|Każdy typ może być przechowywany w zmiennej typu`Object`|  
|[SByte](sbyte-data-type.md)|<xref:System.SByte>|1 bajt|-128 do 127 (podpisane)|  
|[Short](short-data-type.md) (Short Integer)|<xref:System.Int16>|2 bajty|-32 768 do 32 767 (podpisane)|  
|[Single](single-data-type.md) (zmiennoprzecinkowe pojedynczej precyzji)|<xref:System.Single>|4 bajty|-3.4028235 e + 38 za pośrednictwem-1.401298 E-45 <sup>†</sup> dla wartości ujemnych;<br /><br /> 1.401298 e-45 za pośrednictwem 3.4028235 E + 38 <sup>†</sup> dla wartości dodatnich|  
|[Ciąg](string-data-type.md) (o zmiennej długości)|<xref:System.String>określonej|Zależy od implementacji platformy|od 0 do około 2 000 000 000 znaków Unicode|  
|[UInteger —](uinteger-data-type.md)|<xref:System.UInt32>|4 bajty|od 0 do 4 294 967 295 (bez znaku)|  
|[ULong](ulong-data-type.md)|<xref:System.UInt64>|8 bajtów|od 0 do 18446744073709551615 są (1.8... E + 19 <sup>†</sup>) (bez znaku)|  
|[Zdefiniowane przez użytkownika](user-defined-data-type.md) (struktura)|(dziedziczy z <xref:System.ValueType> )|Zależy od implementacji platformy|Każdy element członkowski struktury ma zakres określony przez jego typ danych i niezależny od zakresów innych elementów członkowskich|  
|[UShort](ushort-data-type.md)|<xref:System.UInt16>|2 bajty|od 0 do 65 535 (bez znaku)|  
  
 <sup>†</sup> W *notacji wykładniczej*"E" odnosi się do potęgi 10. So 3.56 E + 2 oznacza 3,56 x 10<sup>2</sup> lub 356 i 3.56 e-2 oznacza 3,56/10<sup>2</sup> lub 0,0356.  
  
> [!NOTE]
> W przypadku ciągów zawierających tekst Użyj <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkcji do konwersji z jednego formatu tekstowego na inny.  
  
 Oprócz określania typu danych w instrukcji deklaracji, można wymusić typ danych niektórych elementów programistycznych przy użyciu znaku typu. Zobacz [znaki typu](../../programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Zużycie pamięci  

 W przypadku deklarowania typu danych podstawowych nie jest bezpieczne, aby założyć, że jego użycie pamięci jest takie samo jak jego nominalna alokacja pamięci masowej. Jest to spowodowane następującymi kwestiami:  
  
- **Przypisanie magazynu.** Środowisko uruchomieniowe języka wspólnego może przypisywać magazyn na podstawie bieżących cech platformy, na których jest wykonywana aplikacja. Jeśli pamięć jest prawie pełna, może spakować zadeklarowane elementy tak blisko siebie, jak to możliwe. W innych przypadkach jego adresy pamięci mogą być wyrównane do naturalnych granic sprzętu w celu zoptymalizowania wydajności.  
  
- **Szerokość platformy.** Przypisanie magazynu na platformę 64-bitową różni się od przypisywania na platformę 32-bitową.  
  
### <a name="composite-data-types"></a>Złożone typy danych  

 Te same zagadnienia dotyczą każdego elementu członkowskiego złożonego typu danych, takiego jak struktura lub tablica. Nie można polegać na prostu przy dodawaniu nominalnych alokacji magazynów elementów członkowskich typu. Ponadto istnieją inne zagadnienia, takie jak następujące:  
  
- **Zwiększenie.** Niektóre typy złożone mają dodatkowe wymagania dotyczące pamięci. Na przykład tablica używa dodatkowej pamięci dla samej tablicy, a także dla każdego wymiaru. Na platformie 32-bitowej ten koszt jest obecnie 12-bajtowy plus 8 bajtów dla każdego wymiaru. Na platformie 64-bitowej ten wymóg jest podwójny.  
  
- **Układ magazynu.** Nie można bezpiecznie założyć, że kolejność przechowywania w pamięci jest taka sama jak kolejność deklaracji. Nie można nawet wprowadzić założeń dotyczących wyrównania bajtów, takich jak granica 2-bajtowe lub 4-bajtowe. W przypadku definiowania klasy lub struktury i należy kontrolować układ magazynu swoich elementów członkowskich, można zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut do klasy lub struktury.  
  
### <a name="object-overhead"></a>Narzut na obiekt  

 `Object`Odwołanie do dowolnego podstawowego lub złożonego typu danych powoduje użycie 4 bajtów oprócz danych zawartych w typie danych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Znaki typu](../../programming-guide/language-features/data-types/type-characters.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
