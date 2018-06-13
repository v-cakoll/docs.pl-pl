---
title: Single — Typ danych (Visual Basic)
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
ms.openlocfilehash: 770961f225b139aaddf34b42327bca63638c725d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590789"
---
# <a name="single-data-type-visual-basic"></a>Single — Typ danych (Visual Basic)
Blokad podpisany IEEE 32-bitowe (4-bajtowych) pojedynczej precyzji liczb zmiennoprzecinkowych z zakresu od - 3.4028235E + 38 do - 1, 401298E-45 dla wartości ujemnych i od 1, 401298E-45 za pośrednictwem 3.4028235E + 38 dla wartości dodatnie. Liczby o pojedynczej dokładności przechowywać zbliżenia liczba rzeczywista.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Single` — typ danych zawierający wartości zmiennoprzecinkowych, które nie wymagają szerokość pełnych danych `Double`. W niektórych przypadkach może mieć możliwość pakietu środowisko uruchomieniowe języka wspólnego programu `Single` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.  
  
 Wartość domyślna `Single` ma wartość 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Precyzja.** Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci. Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Rozszerzanie.** `Single` Rozszerzenie typu danych do `Double`. Oznacza to, że można przekonwertować `Single` do `Double` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Końcowe zero.** Typy danych zmiennoprzecinkowych nie mają żadnych wewnętrznej reprezentacji końcowych 0 znaków. Na przykład one rozróżnia 4.2000 i 4.2. W rezultacie znakami 0 nie jest wyświetlana podczas wyświetlania lub drukowania wartości zmiennoprzecinkowych.  
  
-   **Znaki typu.** Znak literalny typu dołączanie `F` do literału wymusza `Single` — typ danych. Dołączanie znak typu identyfikator `!` dla wszystkich identyfikatorów wymusza `Single`.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Single?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Single?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal, typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
