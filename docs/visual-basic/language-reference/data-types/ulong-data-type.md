---
title: ULong, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: ee9297ae917345d44d8e630bd09beea2245b56da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415521"
---
# <a name="ulong-data-type-visual-basic"></a>ULong — Typ danych (Visual Basic)

Przechowuje niepodpisane liczby całkowite 64-bitowe (8-bajtowe) w zakresie wartości z zakresu od 0 do 18446744073709551615 są (więcej niż 1,84 razy 10 ^ 19).

## <a name="remarks"></a>Uwagi

Użyj `ULong` typu danych, aby zawierać dane binarne za duże `UInteger` lub największa możliwa liczba całkowita bez znaku.

Wartość domyślna `ULong` to 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `ULong` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `ULong` (to jest, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 7 934 076 125 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `ULong` wartości.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `UL` `ul` [znak](../../programming-guide/language-features/data-types/type-characters.md) lub, aby zauważyć `ULong` Typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Liczby ujemne.** Ponieważ `ULong` jest typem bez znaku, nie może reprezentować liczby ujemnej. W przypadku użycia jednoargumentowego operatora minus ( `-` ) w wyrażeniu, którego typem jest typ `ULong` , Visual Basic konwertuje wyrażenie na `Decimal` pierwsze.

- **Zgodność ze specyfikacją CLS.** `ULong`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `ulong` mogą mieć różną szerokość danych (32 bitów) w innych środowiskach. Jeśli przekazujesz argument 32-bitowy do takiego składnika, zadeklaruj go jako `UInteger` zamiast `ULong` w kodzie zarządzanym Visual Basic.

  Ponadto Automatyzacja nie obsługuje 64-bitowych liczb całkowitych w systemie Windows 95, Windows 98, Windows ME lub Windows 2000. Nie można przekazać argumentu Visual Basic `ULong` do składnika automatyzacji na tych platformach.

- **Rozszerzającą.** `ULong`Typ danych poszerza do `Decimal` , `Single` , i `Double` . Oznacza to, że można dokonać konwersji `ULong` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** Dołączanie znaków literału `UL` do literału wymusza jego do `ULong` typu danych. `ULong`nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.UInt64?displayProperty=nameWithType> strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.UInt64>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
