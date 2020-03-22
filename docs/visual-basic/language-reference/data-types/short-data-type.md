---
title: Short — typ danych
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400730"
---
# <a name="short-data-type-visual-basic"></a>Krótki typ danych (Visual Basic)

Posiada podpisane 16-bitowe (2-bajtowe) liczby całkowite o wartości od -32 768 do 32 767.  
  
## <a name="remarks"></a>Uwagi  

 Użyj `Short` typu danych, aby zawierać wartości całkowite, które nie `Integer`wymagają pełnej szerokości danych . W niektórych przypadkach środowisko wykonawcze `Short` języka wspólnego można spakować zmienne ściśle razem i zapisać zużycie pamięci.  
  
 Wartość domyślna `Short` to 0.  
  
## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `Short` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli litera liczba całkowita znajduje się `Short` poza zakresem (oznacza <xref:System.Int16.MinValue?displayProperty=nameWithType> to, <xref:System.Int16.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 1034, które są reprezentowane jako dziesiętne, szesnastkowe i binarne `Short` literały są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na wartości.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały liczbowe mogą również `S` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) typu `Short` oznaczającego typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Poszerzenie.** Typ `Short` danych rozszerza `Integer`się `Long` `Decimal`do `Single`, `Double`, , , lub . Oznacza to, `Short` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.  
  
- **Wpisz znaki.** Dołączenie znaku literału `S` do literału wymusza go do `Short` typu danych. `Short`nie ma znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.Int16?displayProperty=nameWithType> jest strukturą.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Int16?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer — Typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
