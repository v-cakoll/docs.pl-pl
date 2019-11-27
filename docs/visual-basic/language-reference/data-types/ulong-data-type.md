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
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343880"
---
# <a name="ulong-data-type-visual-basic"></a>ULong — Typ danych (Visual Basic)

Przechowuje niepodpisane liczby całkowite 64-bitowe (8-bajtowe) w zakresie wartości z zakresu od 0 do 18446744073709551615 są (więcej niż 1,84 razy 10 ^ 19).

## <a name="remarks"></a>Uwagi

Użyj `ULong` typ danych, aby zawierać dane binarne zbyt duże dla `UInteger`, lub największą liczbę wartości bez znaku.

Wartość domyślna `ULong` wynosi 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `ULong`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `ULong` (czyli jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 7 934 076 125 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `ULong`.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) `UL` lub `ul`, aby zauważyć `ULong` typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Liczby ujemne.** Ponieważ `ULong` jest typem bez znaku, nie może reprezentować liczby ujemnej. Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `ULong`, Visual Basic konwertuje wyrażenie na `Decimal` jako pierwsze.

- **Zgodność ze specyfikacją CLS.** `ULong` typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `ulong` mogą mieć różną szerokość danych (32 bitów) w innych środowiskach. Jeśli przekazujesz argument 32-bitowy do takiego składnika, zadeklaruj go jako `UInteger` zamiast `ULong` w zarządzanym kodzie Visual Basic.

  Ponadto Automatyzacja nie obsługuje 64-bitowych liczb całkowitych w systemie Windows 95, Windows 98, Windows ME lub Windows 2000. Nie można przekazać Visual Basicgo argumentu `ULong` do składnika automatyzacji na tych platformach.

- **Rozszerzającą.** Typ danych `ULong` rozszerza `Decimal`, `Single`i `Double`. Oznacza to, że można skonwertować `ULong` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** Dołączanie znaków literału `UL` do literału wymusza `ULong` do typu danych. `ULong` nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.UInt64?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.UInt64>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
