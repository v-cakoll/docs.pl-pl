---
title: SByte — Typ danych (Visual Basic)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: a962200195002858257b92e92e0dd1383d4fb2d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582519"
---
# <a name="sbyte-data-type-visual-basic"></a>Typ danych (Visual Basic)

Przechowuje 8-bitową liczbę całkowitą ze znakiem, która ma wartość z zakresu od-128 do 127.

## <a name="remarks"></a>Uwagi

Użyj `SByte` typ danych, aby zawierać wartości całkowite, które nie wymagają pełnej szerokości danych `Integer`, a nawet połowę szerokości danych `Short`. W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może być w stanie spakować zmienne `SByte` blisko siebie i zaoszczędzić użycie pamięci.

Wartość domyślna `SByte` wynosi 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `SByte`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.

W poniższym przykładzie liczby całkowite równe-102 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `SByte`. Ten przykład wymaga skompilowania przy użyciu przełącznika kompilatora `/removeintchecks`.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Jeśli literał liczby całkowitej znajduje się poza zakresem `SByte` (czyli jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji. Gdy literał typu Integer nie ma sufiksu, zostanie wywnioskowana [Liczba całkowita](integer-data-type.md) . Jeśli literał liczby całkowitej znajduje się poza zakresem typu `Integer`, jest wywnioskowana wartość [Long](long-data-type.md) . Oznacza to, że w poprzednich przykładach literały numeryczne `0x9A` i `0b10011010` są interpretowane jako 32-bitowe podpisane liczby całkowite o wartości 156, która przekracza <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Aby pomyślnie skompilować kod, który przypisuje niedziesiętną liczbę całkowitą do `SByte`, można wykonać jedną z następujących czynności:

- Wyłącz sprawdzanie granic liczby całkowitej przez skompilowanie przy użyciu przełącznika kompilatora `/removeintchecks`.

- Użyj [znaku typu](../../programming-guide/language-features/data-types/type-characters.md) , aby jawnie zdefiniować wartość literału, która ma zostać przypisana do `SByte`. Poniższy przykład przypisuje literał ujemny `Short` wartość do `SByte`. Należy pamiętać, że w przypadku liczb ujemnych należy ustawić dużą kolejność wyrazów o wysokiej kolejności w literale numerycznym. W przypadku naszego przykładu jest to bit 15 wartości literału `Short` wartość.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zgodność ze specyfikacją CLS.** @No__t_0 typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.

- **Rozszerzającą.** Typ danych `SByte` poszerza do `Short`, `Integer`, `Long`, `Decimal`, `Single` i `Double`. Oznacza to, że można skonwertować `SByte` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** `SByte` nie ma znaku typu literału lub typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.SByte?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.SByte?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
