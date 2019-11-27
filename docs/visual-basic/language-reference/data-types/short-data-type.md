---
title: Short, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343936"
---
# <a name="short-data-type-visual-basic"></a>Short — Typ danych (Visual Basic)

Przechowuje 16-bitowe (2-bajtowe) liczby całkowite z zakresu od-32 768 do 32 767.  
  
## <a name="remarks"></a>Uwagi  

 Użyj `Short` typ danych, aby zawierać wartości całkowite, które nie wymagają pełnej szerokości danych `Integer`. W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może wspólnie spakować zmienne `Short` i zaoszczędzić użycie pamięci.  
  
 Wartość domyślna `Short` wynosi 0.  
  
## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `Short`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `Short` (czyli jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 1 034, które są reprezentowane jako dziesiętne, szesnastkowe i literały binarne, są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na wartości `Short`.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `S` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Short` typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Rozszerzającą.** Typ danych `Short` poszerza do `Integer`, `Long`, `Decimal`, `Single`lub `Double`. Oznacza to, że można skonwertować `Short` do dowolnego jednego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaku typu literału `S` do literału wymusza go do `Short` typu danych. `Short` nie ma znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Int16?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
