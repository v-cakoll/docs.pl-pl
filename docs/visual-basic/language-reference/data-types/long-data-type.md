---
title: Long, typ danych
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
ms.openlocfilehash: 7c076cd2198c85560f7c63c69e051697966c9524
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415599"
---
# <a name="long-data-type-visual-basic"></a>Long — typ danych (Visual Basic)

Przechowuje podpisaną 64-bitową (8-bajtową) liczbę całkowitą z zakresu od-zakresu od do 9 223 372 036 854 775 807 (9.2... E + 18).

## <a name="remarks"></a>Uwagi

Użyj `Long` typu danych, aby zawierać liczby całkowite, które są zbyt duże, aby mieściły się w `Integer` typie danych.

Wartość domyślna `Long` to 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `Long` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `Long` (to jest, jeśli jest mniejszy niż <xref:System.Int64.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.Int64.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 4 294 967 296 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `Long` wartości.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `L` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Long` Typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że `Long` w innych środowiskach ma inną szerokość danych (32 bitów). Jeśli przekazujesz argument 32-bitowy do takiego składnika, zadeklaruj go jako `Integer` zamiast `Long` w nowym kodzie Visual Basic.

- **Rozszerzającą.** `Long`Typ danych poszerza do `Decimal` , `Single` , lub `Double` . Oznacza to, że można przekonwertować `Long` na jeden z tych typów, bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** Dołączanie znaku typu literału `L` do literału wymusza jego `Long` Typ danych. Dołączanie znaku typu identyfikatora `&` do dowolnego identyfikatora zmusza go do `Long` .

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Int64?displayProperty=nameWithType> strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.Int64>
- [Typy danych](index.md)
- [Integer, typ danych](integer-data-type.md)
- [Short, typ danych](short-data-type.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
