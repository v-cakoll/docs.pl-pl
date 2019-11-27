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
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343916"
---
# <a name="single-data-type-visual-basic"></a>Single — Typ danych (Visual Basic)

Przechowuje podpisane cyfry IEEE 32-bit (4-bajtowe) liczby zmiennoprzecinkowe o pojedynczej precyzji w zakresie wartości od-3.4028235 E + 38 do-1.401298 E-45 dla wartości ujemnych i od 1.401298 E-45 przez 3.4028235 E + 38 dla wartości dodatnich. Liczby o pojedynczej precyzji przechowują przybliżoną liczbę rzeczywistą.  
  
## <a name="remarks"></a>Uwagi  

 Użyj `Single` typ danych, aby zawierać wartości zmiennoprzecinkowe, które nie wymagają pełnej szerokości danych `Double`. W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może być w stanie spakować zmienne `Single` blisko siebie i zaoszczędzić użycie pamięci.  
  
 Wartość domyślna `Single` wynosi 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Dokładne.** Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci. Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównanie wartości i operator `Mod`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Rozszerzającą.** Typ danych `Single` poszerza do `Double`. Oznacza to, że można skonwertować `Single` na `Double` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Końcowe zera.** Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji znaków kończących 0. Na przykład nie różnią się od 4,2000 do 4,2. W związku z tym po wyświetleniu lub wydrukowaniu wartości zmiennoprzecinkowych nie są wyświetlane znaki końcowe 0.  
  
- **Znaki typu.** Dołączanie znaku typu literału `F` do literału wymusza go do `Single` typu danych. Dołączanie znaku typu identyfikatora `!` do dowolnego identyfikatora wymusza `Single`.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Single?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal, typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
