---
title: SByte — Typ danych
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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400793"
---
# <a name="sbyte-data-type-visual-basic"></a>Typ danych SByte (Visual Basic)

Przechowuje podpisane 8-bitowe (1-bajtowe) liczby całkowite o wartości od -128 do 127.

## <a name="remarks"></a>Uwagi

Użyj `SByte` typu danych, aby zawierać wartości całkowite, które nie `Integer` wymagają pełnej szerokości `Short`danych lub nawet połowy szerokości danych . W niektórych przypadkach środowisko uruchomieniowe języka `SByte` wspólnego może być w stanie spakować zmienne ściśle razem i zapisać zużycie pamięci.

Wartość domyślna `SByte` to 0.

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `SByte` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.

W poniższym przykładzie liczby całkowite równe -102, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `SByte` wartości. W tym przykładzie wymaga `/removeintchecks` kompilacji z przełącznikiem kompilatora.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Jeśli litera liczba całkowita znajduje się `SByte` poza zakresem (oznacza <xref:System.SByte.MinValue?displayProperty=nameWithType> to, <xref:System.SByte.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji. Gdy litera liczba całkowita nie ma sufiksu, [liczba całkowita](integer-data-type.md) jest wywnioskowana. Jeśli literał liczby całkowitej znajduje się `Integer` poza zakresem typu, [Long](long-data-type.md) jest wywnioskowane. Oznacza to, że w poprzednich przykładach literały `0x9A` `0b10011010` liczbowe i są interpretowane jako 32-bitowe podpisane liczby całkowite <xref:System.SByte.MaxValue?displayProperty=nameWithType>o wartości 156, która przekracza . Aby pomyślnie skompilować kod w ten sposób, który przypisuje `SByte`liczbę całkowitą bez miejsca do przecinka dziesiętnego do , można wykonać jedną z następujących czynności:

- Wyłącz sprawdzanie granic liczby całkowitej, `/removeintchecks` kompilując za pomocą przełącznika kompilatora.

- Użyj [znaku tekstowego,](../../programming-guide/language-features/data-types/type-characters.md) aby jawnie zdefiniować wartość literału, którą chcesz przypisać do pliku `SByte`. Poniższy przykład przypisuje ujemną `Short` wartość `SByte`literału do pliku . Należy zauważyć, że w przypadku liczb ujemnych należy ustawić bit wysokiego rzędu słowa wysokiego rzędu literału liczbowego. W przypadku naszego przykładu jest to nieco 15 wartości literału. `Short`

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zgodność z CLS.** Typ `SByte` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.

- **Poszerzenie.** Typ `SByte` danych rozszerza `Short`się `Integer` `Long`do `Decimal` `Single`, `Double`, , , i . Oznacza to, `SByte` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.

- **Wpisz znaki.** `SByte`nie ma znaku literału ani znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.SByte?displayProperty=nameWithType> jest strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.SByte?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer — Typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
