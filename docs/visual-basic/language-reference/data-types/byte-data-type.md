---
title: Byte — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b106005ff07f55e05ae66dba94041cd8b5c24bb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732147"
---
# <a name="byte-data-type-visual-basic"></a>Byte — typ danych (Visual Basic)
Przechowuje 8-bitowa (1-bajtowe) liczb całkowitych bez znaku z zakresu wartości z zakresu od 0 do 255.

## <a name="remarks"></a>Uwagi

Użyj `Byte` typ danych, aby zawierać dane binarne.  
  
Wartość domyślna `Byte` wynosi 0.

## <a name="literal-assignments"></a>Literał przypisania

Można zadeklarować i zainicjować `Byte` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego. Jeśli literał typu całkowitego jest poza zakresem `Byte` (to znaczy, jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 201, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `byte` wartości.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Liczby ujemne.** Ponieważ `Byte` jest typ bez znaku, go nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `Byte`, Visual Basic konwertuje wyrażenie które ma `Short` pierwszy.
  
-   **Konwersje formatu.** W przypadku języka Visual Basic odczytuje lub zapisuje pliki lub wywoływanych przez nią bibliotek DLL, metod i właściwości, może automatycznie konwertować między formatami danych. Dane binarne przechowywane w `Byte` zmienne i tablice są zachowywane w trakcie takie konwersje formatu. Nie należy używać `String` zmiennej dla danych binarnych, ponieważ jego zawartość, mogą zostać uszkodzone podczas konwersji między formatami ANSI i Unicode.

-   **Rozszerzanie.** `Byte` — Typ danych rozszerza się na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, lub `Double`. Oznacza to, że możesz przekonwertować `Byte` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.
  
-   **Znaki typu.** `Byte` nie ma znak literalny typu lub znak typu identyfikator.

-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Byte?displayProperty=nameWithType> struktury.

## <a name="example"></a>Przykład

 W poniższym przykładzie `b` jest `Byte` zmiennej. Instrukcje pokazują zakres zmiennej i stosowania operatory przesunięcia bitowego w odniesieniu do niego.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Zobacz też

 <xref:System.Byte?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
