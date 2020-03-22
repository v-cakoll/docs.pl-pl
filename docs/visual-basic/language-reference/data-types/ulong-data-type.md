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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400702"
---
# <a name="ulong-data-type-visual-basic"></a>UDlić typ danych (Visual Basic)

Posiada niepodpisane 64-bitowe (8-bajtowe) liczby całkowite o wartości od 0 do 18 446 744 073 709 551 615 (ponad 1,84 razy 10 ^ 19).

## <a name="remarks"></a>Uwagi

Użyj `ULong` typu danych, aby zawierać `UInteger`dane binarne zbyt duże dla lub największe możliwe niepodpisane wartości całkowite.

Wartość domyślna `ULong` to 0.

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `ULong` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli litera liczba całkowita znajduje się `ULong` poza zakresem (oznacza <xref:System.UInt64.MinValue?displayProperty=nameWithType> to, <xref:System.UInt64.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `ULong` wartości.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały liczbowe mogą również `UL` `ul` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) lub `ULong` typ oznaczania typu danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Liczby ujemne.** Ponieważ `ULong` jest typem niepodpisanym, nie może reprezentować liczby ujemnej. Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `ULong`visual basic konwertuje wyrażenie na `Decimal` pierwsze.

- **Zgodność z CLS.** Typ `ULong` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.

- **Zagadnienia międzyoperacyjne.** Jeśli są interfacing z składników nie zostały napisane dla .NET Framework, na przykład automatyzacji lub COM obiektów, należy pamiętać, że typy, takie jak `ulong` może mieć inną szerokość danych (32 bity) w innych środowiskach. Jeśli przekazujesz 32-bitowy argument do takiego składnika, zadeklaruj go jako `UInteger` zamiast `ULong` w zarządzanym kodzie języka Visual Basic.

  Ponadto automatyzacja nie obsługuje 64-bitowych liczby całkowite w systemach Windows 95, Windows 98, Windows ME lub Windows 2000. Nie można przekazać `ULong` argumentu języka Visual Basic do składnika automatyzacji na tych platformach.

- **Poszerzenie.** Typ `ULong` danych rozszerza `Decimal`się `Single`na `Double`, i . Oznacza to, `ULong` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.

- **Wpisz znaki.** Dołączenie znaków `UL` typu literału do literału `ULong` wymusza go do typu danych. `ULong`nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.UInt64?displayProperty=nameWithType> jest strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.UInt64>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
