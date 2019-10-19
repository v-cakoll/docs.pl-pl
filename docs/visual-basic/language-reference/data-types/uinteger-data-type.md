---
title: UInteger — — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 1ae0cbd3a518bf863a3c57f50934837a486d2901
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583135"
---
# <a name="uinteger-data-type"></a>UInteger — Typ danych

Przechowuje niepodpisane liczby całkowite 32-bitowe (4-bajtowe) w zakresie wartości z zakresu od 0 do 4 294 967 295.

## <a name="remarks"></a>Uwagi

Typ danych `UInteger` zapewnia największą wartość bez znaku w najbardziej wydajnej szerokości danych.

Wartość domyślna `UInteger` wynosi 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `UInteger`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `UInteger` (czyli jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 3 000 000 000 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) `UI` lub `ui`, aby zauważyć `UInteger` typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Porady dotyczące programowania

Typy danych `UInteger` i `Integer` zapewniają optymalną wydajność procesora 32-bitowego, ponieważ mniejsze typy całkowite (`UShort`, `Short`, `Byte` i `SByte`), nawet jeśli używają mniejszej liczby bitów, Załaduj więcej czasu , przechowuj i pobieraj.

- **Liczby ujemne.** Ponieważ `UInteger` jest typem bez znaku, nie może reprezentować liczby ujemnej. Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `UInteger`, Visual Basic konwertuje wyrażenie na `Long` jako pierwsze.

- **Zgodność ze specyfikacją CLS.** @No__t_0 typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `uint` mogą mieć różną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.

- **Rozszerzającą.** Typ danych `UInteger` poszerza do `Long`, `ULong`, `Decimal`, `Single` i `Double`. Oznacza to, że można skonwertować `UInteger` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** Dołączanie znaków literału `UI` do literału wymusza `UInteger` do typu danych. `UInteger` nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.UInt32>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
