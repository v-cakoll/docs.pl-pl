---
title: Long — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400814"
---
# <a name="long-data-type-visual-basic"></a>Długi typ danych (Visual Basic)

Posiada podpisane 64-bitowe (8-bajtowe) liczby całkowite o wartości od -9 223 372 036 854 775 808 do 9 223 372 036 854 775 807 (9,2...E+18).

## <a name="remarks"></a>Uwagi

Użyj `Long` typu danych, aby zawierać liczby całkowite, które są `Integer` zbyt duże, aby zmieścić się w typie danych.

Wartość domyślna `Long` to 0.

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `Long` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli litera liczba całkowita znajduje się `Long` poza zakresem (oznacza <xref:System.Int64.MinValue?displayProperty=nameWithType> to, <xref:System.Int64.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 4,294,967,296, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `Long` wartości.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały liczbowe mogą również `L` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) typu `Long` oznaczającego typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zagadnienia międzyoperacyjne.** Jeśli łączysz się ze składnikami nieuznawane dla programu .NET Framework, `Long` na przykład automatyzacji lub COM obiektów, należy pamiętać, że ma inną szerokość danych (32 bity) w innych środowiskach. Jeśli przekazujesz 32-bitowy argument do takiego składnika, zadeklaruj go jako `Integer` zamiast `Long` w nowym kodzie języka Visual Basic.

- **Poszerzenie.** Typ `Long` danych rozszerza `Decimal`się `Single`do `Double`, lub . Oznacza to, `Long` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.

- **Wpisz znaki.** Dołączenie znaku literału `L` do literału wymusza go do `Long` typu danych. Dołączenie znaku `&` typu identyfikatora do dowolnego identyfikatora wymusza jego `Long`

- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.Int64?displayProperty=nameWithType> jest strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.Int64>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Integer — Typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
