---
title: SByte, typ danych
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
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415573"
---
# <a name="sbyte-data-type-visual-basic"></a>Typ danych (Visual Basic)

Przechowuje 8-bitową liczbę całkowitą ze znakiem, która ma wartość z zakresu od-128 do 127.

## <a name="remarks"></a>Uwagi

Użyj `SByte` typu danych, aby zawierać wartości całkowite, które nie wymagają pełnej szerokości danych, `Integer` a nawet połówkowej szerokości danych `Short` . W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może mieć ścisłe spakowanie `SByte` zmiennych i oszczędność zużycia pamięci.

Wartość domyślna `SByte` to 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `SByte` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.

W poniższym przykładzie liczby całkowite równe-102 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `SByte` wartości. Ten przykład wymaga skompilowania z `/removeintchecks` przełącznikiem kompilatora.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Jeśli literał liczby całkowitej znajduje się poza zakresem `SByte` (to jest, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.SByte.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji. Gdy literał typu Integer nie ma sufiksu, zostanie wywnioskowana [Liczba całkowita](integer-data-type.md) . Jeśli literał liczby całkowitej jest poza zakresem `Integer` typu, jest wywnioskowana wartość [Long](long-data-type.md) . Oznacza to, że w poprzednich przykładach literały liczbowe `0x9A` i `0b10011010` są interpretowane jako 32-bitowe liczby całkowite ze znakiem o wartości 156, które przekraczają <xref:System.SByte.MaxValue?displayProperty=nameWithType> . Aby pomyślnie skompilować kod, który przypisuje niedziesiętną liczbę całkowitą do `SByte` , można wykonać jedną z następujących czynności:

- Wyłącz sprawdzanie granic liczby całkowitej przez skompilowanie z `/removeintchecks` przełącznikiem kompilatora.

- Użyj [znaku typu](../../programming-guide/language-features/data-types/type-characters.md) , aby jawnie zdefiniować wartość literału, która ma zostać przypisana do `SByte` . Poniższy przykład przypisuje ujemną wartość literału `Short` do `SByte` . Należy pamiętać, że w przypadku liczb ujemnych należy ustawić dużą kolejność wyrazów o wysokiej kolejności w literale numerycznym. W przypadku naszego przykładu jest to bit 15 wartości literału `Short` .

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zgodność ze specyfikacją CLS.** `SByte`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.

- **Rozszerzającą.** `SByte`Typ danych poszerza do `Short` ,,, `Integer` , `Long` `Decimal` `Single` , i `Double` . Oznacza to, że można dokonać konwersji `SByte` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** `SByte`nie ma znaku typu literału lub znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.SByte?displayProperty=nameWithType> strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.SByte?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Short, typ danych](short-data-type.md)
- [Integer, typ danych](integer-data-type.md)
- [Long, typ danych](long-data-type.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
