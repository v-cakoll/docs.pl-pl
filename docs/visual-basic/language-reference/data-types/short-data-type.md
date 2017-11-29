---
title: "Short — Typ danych (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords: vb.Short
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
ms.openlocfilehash: fef948debed69cf9fb7b0e6bb65eb0ddbe497a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="short-data-type-visual-basic"></a>Short — typ danych (Visual Basic)
Blokad podpisany 16-bitowych liczb całkowitych (2-bajtowych) o wartości od-32 768 do 32 767.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Short` — typ danych zawierający wartości całkowite, które nie wymagają szerokość pełnych danych `Integer`. W niektórych przypadkach można pakietu środowisko uruchomieniowe języka wspólnego programu `Short` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.  
  
 Wartość domyślna `Short` ma wartość 0.  
  
## <a name="literal-assignments"></a>Przydziały literału

Można zadeklarować i zainicjuj `Short` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli liczba całkowita literału jest poza zakresem `Short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `Short` wartości.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Literały numeryczne mogą również obejmować `S` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Short` typu danych, jak przedstawiono na poniższym przykładzie.

```vb
Dim number = &H0326S
```

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Rozszerzanie.** `Short` Rozszerzenie typu danych do `Integer`, `Long`, `Decimal`, `Single`, lub `Double`. Oznacza to, że można przekonwertować `Short` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znak literalny typu dołączanie `S` do literału wymusza `Short` — typ danych. `Short`nie ma identyfikatora typu znaku.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Int16?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz także

 <xref:System.Int16?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Integer — typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long — typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
