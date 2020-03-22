---
title: UInteger — Typ danych
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
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400786"
---
# <a name="uinteger-data-type"></a>UInteger — Typ danych

Przechowuje niepodpisane 32-bitowe (4-bajtowe) liczby całkowite o wartości od 0 do 4 294 967 295.

## <a name="remarks"></a>Uwagi

Typ `UInteger` danych zapewnia największą niepodpisaną wartość w najbardziej wydajnej szerokości danych.

Wartość domyślna `UInteger` to 0.

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `UInteger` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli litera liczba całkowita znajduje się `UInteger` poza zakresem (oznacza <xref:System.UInt32.MinValue?displayProperty=nameWithType> to, <xref:System.UInt32.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 3,000,000,000, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `UInteger` wartości.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały liczbowe mogą również `UI` `ui` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) lub `UInteger` typ oznaczania typu danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Porady dotyczące programowania

`UInteger` Typy `Integer` danych zapewniają optymalną wydajność procesora 32-bitowego, ponieważ`UShort` `Short`mniejsze `Byte`typy całkowite ( , , , i `SByte`), nawet jeśli używają mniejszej liczby bitów, zajmuje więcej czasu na ładowanie, przechowywanie i pobieranie.

- **Liczby ujemne.** Ponieważ `UInteger` jest typem niepodpisanym, nie może reprezentować liczby ujemnej. Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `UInteger`visual basic konwertuje wyrażenie na `Long` pierwsze.

- **Zgodność z CLS.** Typ `UInteger` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.

- **Zagadnienia międzyoperacyjne.** Jeśli są interfacing z składników nie zostały napisane dla .NET Framework, na przykład automatyzacji lub COM obiektów, należy pamiętać, że typy, takie jak `uint` może mieć inną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz 16-bitowy argument do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.

- **Poszerzenie.** Typ `UInteger` danych rozszerza `Long`się `ULong` `Decimal`do `Single`, `Double`, , i . Oznacza to, `UInteger` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.

- **Wpisz znaki.** Dołączenie znaków `UI` typu literału do literału `UInteger` wymusza go do typu danych. `UInteger`nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.UInt32?displayProperty=nameWithType> jest strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.UInt32>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
