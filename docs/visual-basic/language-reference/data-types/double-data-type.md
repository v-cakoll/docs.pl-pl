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
ms.openlocfilehash: 899554f427ac77ead465752c35e51ca88d045763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415637"
---
# <a name="double-data-type-visual-basic"></a>Double — Typ danych (Visual Basic)

Przechowuje podpisane cyfry IEEE 64-bit (8-bajtowe) liczby zmiennoprzecinkowe podwójnej precyzji, które obejmują wartość z-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 dla wartości ujemnych i od 4.94065645841246544 E-324 do 1.79769313486231570 E + 308 dla wartości dodatnich. Numery podwójnej precyzji przechowują przybliżoną liczbę rzeczywistą.

## <a name="remarks"></a>Uwagi

`Double`Typ danych zapewnia największą i najmniejszą możliwą liczbę wielkości.

Wartość domyślna `Double` to 0.

## <a name="programming-tips"></a>Porady dla programistów

- **Dokładne.** Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównywanie wartości i `Mod` operator. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Końcowe zera.** Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji końcowych znaków. Na przykład nie różnią się od 4,2000 do 4,2. W związku z tym końcowe znaki nie są wyświetlane podczas wyświetlania lub drukowania wartości zmiennoprzecinkowych.

- **Znaki typu.** Dołączanie znaku typu literału `R` do literału wymusza jego `Double` Typ danych. Na przykład, jeśli następuje wartość typu Integer `R` , wartość zostanie zmieniona na `Double` .

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  Dołączanie znaku typu identyfikatora `#` do dowolnego identyfikatora zmusza go do `Double` . W poniższym przykładzie zmienna `num` jest wpisana jako `Double` :

  ```vb
  Dim num# = 3
  ```

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Double?displayProperty=nameWithType> strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.Double?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Decimal, typ danych](decimal-data-type.md)
- [Single, typ danych](single-data-type.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaki typu](../../programming-guide/language-features/data-types/type-characters.md)
