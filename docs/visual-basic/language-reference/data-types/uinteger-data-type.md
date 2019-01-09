---
title: Uinteger — typ danych (Visual Basic)
ms.date: 01/31/2018
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
ms.openlocfilehash: 929197d8e8f9ab031e72e7d332422b388a22ea95
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146059"
---
# <a name="uinteger-data-type"></a>UInteger — Typ danych

Przechowuje 32-bitowe (4-bajtową) liczb całkowitych bez znaku z zakresu od 0 do 4 294 967 295.  
  
## <a name="remarks"></a>Uwagi

 `UInteger` — Typ danych zapewnia największą wartość bez znaku w najbardziej efektywny sposób szerokość danych.  
  
 Wartość domyślna `UInteger` wynosi 0.  
  
## <a name="literal-assignments"></a>Literał przypisania

Można zadeklarować i zainicjować `UInteger` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego. Jeśli literał liczby całkowitej jest poza zakresem `UInteger` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `UInteger` wartości.
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `UI` lub `ui` [wpisz znak](../../programming-guide/language-features/data-types/type-characters.md) do oznaczania `UInteger` typu danych, co ilustruje poniższy przykład.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Porady dotyczące programowania

 `UInteger` i `Integer` typy danych zapewnić optymalną wydajność na 32-bitowym procesorze, ponieważ mniejszych typów całkowitych (`UShort`, `Short`, `Byte`, i `SByte`), nawet jeśli korzystają z mniejszą liczbą bitów, zajmują więcej czasu Ładowanie, przechowywania i pobierania.  
  
-   **Liczby ujemne.** Ponieważ `UInteger` jest typ bez znaku, go nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `UInteger`, Visual Basic konwertuje wyrażenie które ma `Long` pierwszy.  
  
-   **Zgodność ze specyfikacją CLS.** `UInteger` Typem danych nie jest częścią [specyfikacja Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.
  
-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, takich jak wpisywany `uint` mogą mieć różną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.  
  
-   **Rozszerzanie.** `UInteger` — Typ danych rozszerza się na `Long`, `ULong`, `Decimal`, `Single`, i `Double`. Oznacza to, że możesz przekonwertować `UInteger` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Dołącza znaki literalne `UI` do literału wymusza `UInteger` typu danych. `UInteger` nie ma identyfikatora typ znaku.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.UInt32?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.UInt32>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
