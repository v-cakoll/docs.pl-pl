---
title: Short — Typ danych (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: eb218a9b72208b13700ebd18dbf588066839203d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930155"
---
# <a name="short-data-type-visual-basic"></a>Short — typ danych (Visual Basic)
Przechowuje podpisany 16-bitowych liczb całkowitych (2-bajtowych), z zakresu wartości od-32 768 za pośrednictwem 32 767 znaków.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Short` typu danych, które zawierają wartości całkowitych, które nie wymagają szerokość pełnych danych `Integer`. W niektórych przypadkach można pakietu środowiska uruchomieniowego języka wspólnego swoje `Short` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.  
  
 Wartość domyślna `Short` wynosi 0.  
  
## <a name="literal-assignments"></a>Literał przypisania

Można zadeklarować i zainicjować `Short` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego. Jeśli literał liczby całkowitej jest poza zakresem `Short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `Short` wartości.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `S` [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Short` typu danych, co ilustruje poniższy przykład.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Rozszerzanie.** `Short` — Typ danych rozszerza się na `Integer`, `Long`, `Decimal`, `Single`, lub `Double`. Oznacza to, że możesz przekonwertować `Short` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Dołączanie znaku typu literał `S` do literału wymusza `Short` typu danych. `Short` nie ma identyfikatora typ znaku.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Int16?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz także

 <xref:System.Int16?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
