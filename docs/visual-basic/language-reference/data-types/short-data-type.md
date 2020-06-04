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
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415560"
---
# <a name="short-data-type-visual-basic"></a>Short — Typ danych (Visual Basic)

Przechowuje 16-bitowe (2-bajtowe) liczby całkowite z zakresu od-32 768 do 32 767.  
  
## <a name="remarks"></a>Uwagi  

 Użyj `Short` typu danych, aby zawierać wartości całkowite, które nie wymagają pełnej szerokości danych `Integer` . W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może ściśle spakować `Short` zmienne i zaoszczędzić użycie pamięci.  
  
 Wartość domyślna `Short` to 0.  
  
## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `Short` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `Short` (to jest, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.Int16.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 1 034 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na `Short` wartości.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `S` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Short` Typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Rozszerzającą.** `Short`Typ danych poszerza do `Integer` ,,, `Long` `Decimal` `Single` lub `Double` . Oznacza to, że można przekonwertować `Short` na jeden z tych typów, bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaku typu literału `S` do literału wymusza jego `Short` Typ danych. `Short`nie ma znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Int16?displayProperty=nameWithType> strukturą.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Int16?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Integer, typ danych](integer-data-type.md)
- [Long, typ danych](long-data-type.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
