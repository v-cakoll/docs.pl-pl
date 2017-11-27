---
title: "SByte — Typ danych (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a>SByte — typ danych (Visual Basic)

Blokad podpisany 8-bitowych liczb całkowitych (1-bajtowy), które wartości w wartość z zakresu od -128 do 127.  
  
## <a name="remarks"></a>Uwagi

Użyj `SByte` — typ danych zawierający wartości całkowite, które nie wymagają szerokość pełnych danych `Integer` , a nawet szerokość połowa danych `Short`. W niektórych przypadkach może mieć możliwość pakietu środowisko uruchomieniowe języka wspólnego programu `SByte` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.

Wartość domyślna `SByte` ma wartość 0.

## <a name="literal-assignments"></a>Przydziały literału
  
Można zadeklarować i zainicjuj `SByte` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.

W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `SByte` wartości. W tym przykładzie wymaga, aby skompilować z `/removeintchecks` przełącznika kompilatora.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Jeśli liczba całkowita literału jest poza zakresem `SByte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji. Gdy całkowitą literału ma nie sufiks [całkowitą](integer-data-type.md) jest wywnioskowany. Jeśli liczba całkowita literału jest poza zakresem `Integer` typu [długi](long-data-type.md) jest wywnioskowany. To oznacza, że w poprzednich przykładach, literałach numerycznych `0x9A` i `0b10011010` będą interpretowane jako 32-bitowych liczb całkowitych ze znakiem z wartością 156, którego rozmiar przekracza <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Aby pomyślnie skompilować kod podobny do tego, który przypisuje podawać liczby całkowitej w celu `SByte`, wykonaj jedną z następujących czynności:

- Wyłącz sprawdzanie granic całkowitych przez kompilowania przy użyciu `/removeintchecks` przełącznika kompilatora.

- Użyj [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) Aby jawnie określić wartość literału, który ma zostać przypisany do `SByte`. W poniższym przykładzie przypisano ujemna literał `Short` do wartości `SByte`. Należy zauważyć, że dla wartości ujemne, musi mieć ustawiony bit znaczących wyrazu znaczących literał liczbowy. W przypadku naszym przykładzie jest to bit 15 literał `Short` wartość.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Porady dotyczące programowania
  
-   **Zgodności ze specyfikacją CLS.** `SByte` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.

-   **Rozszerzanie.** `SByte` Rozszerzenie typu danych do `Short`, `Integer`, `Long`, `Decimal`, `Single`, i `Double`. Oznacza to, że można przekonwertować `SByte` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.
  
-   **Znaki typu.** `SByte`nie ma znak literalny typu ani znak typu identyfikator.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.SByte?displayProperty=nameWithType> struktury.
  
## <a name="see-also"></a>Zobacz także

 <xref:System.SByte?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Short — typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Integer — typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long — typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
