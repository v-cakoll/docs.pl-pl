---
title: Double, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 347b5c7b7af4c4aafec0f91aca46a8cf640236b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344018"
---
# <a name="double-data-type-visual-basic"></a>Double — Typ danych (Visual Basic)

Przechowuje podpisane cyfry IEEE 64-bitowe (8-bajtowe) liczby zmiennoprzecinkowe o podwójnej precyzji, które obejmują wartość z-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 dla wartości ujemnych i z 4.94065645841246544 E-324 przez 1.79769313486231570 E + 308 dla wartości dodatnie. Numery podwójnej precyzji przechowują przybliżoną liczbę rzeczywistą.

## <a name="remarks"></a>Uwagi

Typ danych `Double` zapewnia największą i najmniejszą liczbę możliwych wielkości dla liczby.

Wartość domyślna `Double` wynosi 0.

## <a name="programming-tips"></a>Porady dla programistów

- **Dokładne.** Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównanie wartości i operator `Mod`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Końcowe zera.** Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji końcowych znaków. Na przykład nie różnią się od 4,2000 do 4,2. W związku z tym końcowe znaki nie są wyświetlane podczas wyświetlania lub drukowania wartości zmiennoprzecinkowych.

- **Znaki typu.** Dołączanie znaku typu literału `R` do literału wymusza go do `Double` typu danych. Na przykład, jeśli po wartości całkowitej następuje `R`, wartość zostanie zmieniona na `Double`.

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  Dołączanie znaku typu identyfikatora `#` do dowolnego identyfikatora wymusza `Double`. W poniższym przykładzie zmienna `num` jest wpisana jako `Double`:

  ```vb
  Dim num# = 3
  ```

- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Double?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Double?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal, typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single, typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
