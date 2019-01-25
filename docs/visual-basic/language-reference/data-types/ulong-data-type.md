---
title: ULong — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 82a2badc1bb22a55f753c9075562db3a5ee0d234
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522963"
---
# <a name="ulong-data-type-visual-basic"></a>Ulong — typ danych (Visual Basic)

Przechowuje 64-bitowych (8-bajtową) liczb całkowitych bez znaku z zakresu od 0 do 18,446,744,073,709,551,615 (10 razy większa od 1.84 ^ 19).  
  
## <a name="remarks"></a>Uwagi

Użyj `ULong` typ danych, aby zawierać dane binarne, które są zbyt duże, aby `UInteger`, lub największa możliwa niepodpisanych liczb całkowitych.  
  
Wartość domyślna `ULong` wynosi 0.

## <a name="literal-assignments"></a>Literał przypisania

Można zadeklarować i zainicjować `ULong` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego. Jeśli literał liczby całkowitej jest poza zakresem `ULong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `ULong` wartości.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `UL` lub `ul` [wpisz znak](../../programming-guide/language-features/data-types/type-characters.md) do oznaczania `ULong` typu danych, co ilustruje poniższy przykład.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Porady dotyczące programowania
  
-   **Liczby ujemne.** Ponieważ `ULong` jest typ bez znaku, go nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `ULong`, Visual Basic konwertuje wyrażenie które ma `Decimal` pierwszy.  
  
-   **CLS Compliance.** `ULong` Typem danych nie jest częścią [specyfikacja Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.  
  
-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, takich jak wpisywany `ulong` mogą mieć różną szerokość danych (32-bitowy) w innych środowiskach. Jeśli przekazujesz 32-bitowy argument do takiego składnika, Zadeklaruj go jako `UInteger` zamiast `ULong` w zarządzanym kodzie języka Visual Basic.  
  
     Ponadto usługi Automation nie obsługuje 64-bitowych liczb całkowitych na Windows 95, Windows 98, Windows ME lub Windows 2000. Nie można przekazać w języku Visual Basic `ULong` argument do składnika usługi Automation na tych platformach.  
  
-   **Rozszerzanie.** `ULong` — Typ danych rozszerza się na `Decimal`, `Single`, i `Double`. Oznacza to, że możesz przekonwertować `ULong` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Dołącza znaki literalne `UL` do literału wymusza `ULong` typu danych. `ULong` nie ma identyfikatora typ znaku.
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.UInt64?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.UInt64>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
