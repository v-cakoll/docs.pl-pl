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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ab72b2ac2678640697e3cfab426e5a7d6d889a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467179"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte — typ danych (Visual Basic)

Przechowuje podpisany (8-bitowa 1-bajtowe) liczby całkowite z zakresu wartości od -128 do 127.  
  
## <a name="remarks"></a>Uwagi

Użyj `SByte` typu danych, które zawierają wartości całkowitych, które nie wymagają szerokość pełnych danych `Integer` , a nawet szerokość danych w wysokości równej połowie `Short`. W niektórych przypadkach może być możliwość pakietu środowiska uruchomieniowego języka wspólnego swoje `SByte` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.

Wartość domyślna `SByte` wynosi 0.

## <a name="literal-assignments"></a>Literał przypisania
  
Można zadeklarować i zainicjować `SByte` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.

W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `SByte` wartości. W tym przykładzie wymaga kompilacji z `/removeintchecks` przełącznika kompilatora.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Jeśli literał liczby całkowitej jest poza zakresem `SByte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji. Gdy literał liczby całkowitej ma Brak przyrostka [całkowitą](integer-data-type.md) została wywnioskowana. Jeśli literał liczby całkowitej jest poza zakresem `Integer` typu [długie](long-data-type.md) została wywnioskowana. Oznacza to, że w poprzednich przykładach literały numeryczne `0x9A` i `0b10011010` są interpretowane jako 32-bitowe liczby całkowite ze znakiem z wartością 156, co powoduje przekroczenie <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Aby pomyślnie skompilować kod tak, który przypisuje niebędący cyfrą dziesiętną liczby całkowitej w celu `SByte`, można wykonać jedną z następujących czynności:

- Wyłącz sprawdzanie granic liczby całkowitej przez kompilowanie za pomocą `/removeintchecks` przełącznika kompilatora.

- Użyj [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) umożliwia jawne zdefiniowanie wartości literału, który chcesz przypisać do `SByte`. Poniższy przykład przypisuje ujemna literał `Short` wartość `SByte`. Należy pamiętać, że dla liczb ujemnych musi być ustawiony bit wyższego rzędu słowo wyższego rzędu literału liczbowego. W przypadku naszym przykładzie jest to bit 15 literału `Short` wartość.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Porady dotyczące programowania
  
-   **Zgodność ze specyfikacją CLS.** `SByte` Typem danych nie jest częścią [specyfikacja Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.

-   **Rozszerzanie.** `SByte` — Typ danych rozszerza się na `Short`, `Integer`, `Long`, `Decimal`, `Single`, i `Double`. Oznacza to, że możesz przekonwertować `SByte` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.
  
-   **Znaki typu.** `SByte` nie ma znak literalny typu lub znak typu identyfikator.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.SByte?displayProperty=nameWithType> struktury.
  
## <a name="see-also"></a>Zobacz także

 <xref:System.SByte?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
