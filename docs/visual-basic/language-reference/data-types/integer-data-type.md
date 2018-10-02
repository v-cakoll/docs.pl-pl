---
title: Integer — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc780cc845bfa6ef52fc9973ef3617d621167af1
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "44177526"
---
# <a name="integer-data-type-visual-basic"></a>Integer — typ danych (Visual Basic)
Przechowuje 32-bitowe (4-bajtowe) liczby całkowite ze znakiem z zakresu wartości od -2 147 483,648 do 2 147 483 647.  
  
## <a name="remarks"></a>Uwagi
 `Integer` — Typ danych zapewnia optymalną wydajność na 32-bitowy procesor. Inne typy całkowitoliczbowe wolniej wczytują się z pamięci i są w niej zapisywane.  
  
 Wartość domyślna `Integer` wynosi 0.  

## <a name="literal-assignments"></a>Literał przypisania

Można zadeklarować i zainicjować `Integer` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego. Jeśli literał liczby całkowitej jest poza zakresem `Integer` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 16,342, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `Integer` wartości.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również obejmować `I` [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Integer` typu danych, co ilustruje poniższy przykład.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, pamiętaj, że `Integer` ma różną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz 16-bitowy argument do takiego składnika, Zadeklaruj go jako `Short` zamiast `Integer` nowego kodu języka Visual Basic.  
  
-   **Rozszerzanie.** `Integer` — Typ danych rozszerza się na `Long`, `Decimal`, `Single`, lub `Double`. Oznacza to, że możesz przekonwertować `Integer` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Znaki typu.** Dołączanie znaku typu literał `I` do literału wymusza `Integer` typu danych. Dołączanie znaku typu identyfikator `%` do jakiegokolwiek identyfikatora wymusza `Integer`.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Int32?displayProperty=nameWithType> struktury.  
  
## <a name="range"></a>Zakres

Jeśli spróbujesz ustawić zmienną typu całkowitoliczbowego na liczbę spoza zakresu dla tego typu, wystąpi błąd. Jeśli spróbujesz ustawić ją na ułamek, liczba jest zaokrąglana w górę lub w dół do najbliższej wartości liczby całkowitej. Jeśli liczba jest jednakowo blisko dwóch wartości całkowitych, wartość jest zaokrąglana do najbliższej parzystej liczby całkowitej. To zachowanie minimalizuje błędy zaokrągleń, które powstają w wyniku konsekwentnego zaokrąglania wartości punktu środkowego w jednym kierunku. W poniższym kodzie pokazano przykłady zaokrąglania.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Zobacz także

<xref:System.Int32?displayProperty=nameWithType>   
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
