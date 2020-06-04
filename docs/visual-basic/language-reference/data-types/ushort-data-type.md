---
title: UShort, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415482"
---
# <a name="ushort-data-type-visual-basic"></a>UShort — Typ danych (Visual Basic)

Przechowuje liczby całkowite (2-bajtowe) bez znaku w zakresie od 0 do 65 535.  
  
## <a name="remarks"></a>Uwagi

 Użyj `UShort` typu danych, aby zawierać dane binarne za duże `Byte` .  
  
 Wartość domyślna `UShort` to 0.  

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `UShort` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `UShort` (to jest, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 65 034 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `UShort` wartości.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `US` `us` [znak](../../programming-guide/language-features/data-types/type-characters.md) lub, aby zauważyć `UShort` Typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Porady dotyczące programowania
  
- **Liczby ujemne.** Ponieważ `UShort` jest typem bez znaku, nie może reprezentować liczby ujemnej. W przypadku użycia jednoargumentowego operatora minus ( `-` ) w wyrażeniu, którego typem jest typ `UShort` , Visual Basic konwertuje wyrażenie na `Integer` pierwsze.  
  
- **Zgodność ze specyfikacją CLS.** `UShort`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.
  
- **Rozszerzającą.** `UShort`Typ danych poszerza do,, `Integer` ,,, `UInteger` `Long` `ULong` `Decimal` `Single` , i `Double` . Oznacza to, że można dokonać konwersji `UShort` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaków literału `US` do literału wymusza jego do `UShort` typu danych. `UShort`nie ma znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.UInt16?displayProperty=nameWithType> strukturą.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.UInt16>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
