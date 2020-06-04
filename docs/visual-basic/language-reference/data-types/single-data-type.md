---
title: Single, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415534"
---
# <a name="single-data-type-visual-basic"></a>Single — Typ danych (Visual Basic)

Przechowuje podpisane cyfry IEEE 32-bit (4-bajtowe) liczby zmiennoprzecinkowe o pojedynczej precyzji w zakresie wartości od-3.4028235 E + 38 do-1.401298 E-45 dla wartości ujemnych i od 1.401298 E-45 przez 3.4028235 E + 38 dla wartości dodatnich. Liczby o pojedynczej precyzji przechowują przybliżoną liczbę rzeczywistą.  
  
## <a name="remarks"></a>Uwagi  

 Użyj `Single` typu danych, aby zawierać wartości zmiennoprzecinkowe, które nie wymagają pełnej szerokości danych `Double` . W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może mieć `Single` ścisłe pakowanie zmiennych i oszczędność zużycia pamięci.  
  
 Wartość domyślna `Single` to 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Dokładne.** Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównywanie wartości i `Mod` operator. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Rozszerzającą.** `Single`Typ danych jest rozszerzany do `Double` . Oznacza to, że można przeprowadzić konwersję `Single` na `Double` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Końcowe zera.** Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji znaków kończących 0. Na przykład nie różnią się od 4,2000 do 4,2. W związku z tym po wyświetleniu lub wydrukowaniu wartości zmiennoprzecinkowych nie są wyświetlane znaki końcowe 0.  
  
- **Znaki typu.** Dołączanie znaku typu literału `F` do literału wymusza jego `Single` Typ danych. Dołączanie znaku typu identyfikatora `!` do dowolnego identyfikatora zmusza go do `Single` .  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Single?displayProperty=nameWithType> strukturą.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Single?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Decimal, typ danych](decimal-data-type.md)
- [Double, typ danych](double-data-type.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
