---
title: "UInteger — Typ danych"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea6d42a604e5a50fab62644034afc82e089792c7
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="uinteger-data-type"></a>UInteger — Typ danych

Blokad 32-bitowe (4-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 4 294 967 295.  
  
## <a name="remarks"></a>Uwagi

 `UInteger` — Typ danych zapewnia największą wartość bez znaku w najbardziej efektywny szerokość danych.  
  
 Wartość domyślna `UInteger` ma wartość 0.  
  
## <a name="literal-assignments"></a>Przydziały literału

Można zadeklarować i zainicjuj `UInteger` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli liczba całkowita literału jest poza zakresem `UInteger` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `UInteger` wartości.
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `UI` lub `ui` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `UInteger` typu danych, jak przedstawiono na poniższym przykładzie.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Porady dotyczące programowania

 `UInteger` i `Integer` typy danych zapewnić optymalną wydajność na 32-bitowego procesora, ponieważ mniejszych typów całkowitych (`UShort`, `Short`, `Byte`, i `SByte`), nawet jeśli korzystają z mniej bits zająć więcej czasu Ładowanie, przechowywania i pobierania.  
  
-   **Wartości ujemne.** Ponieważ `UInteger` jest typu unsigned, nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `UInteger`, Visual Basic konwertuje wyrażenie `Long` pierwszy.  
  
-   **Zgodności ze specyfikacją CLS.** `UInteger` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy, takich jak `uint` może mieć szerokość różnych danych (16 bitów) w innych środowiskach. Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.  
  
-   **Rozszerzanie.** `UInteger` Rozszerzenie typu danych do `Long`, `ULong`, `Decimal`, `Single`, i `Double`. Oznacza to, że można przekonwertować `UInteger` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Znaki literalne dołączanie `UI` do literału wymusza `UInteger` — typ danych. `UInteger`nie ma identyfikatora typu znaku.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.UInt32?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.UInt32>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
