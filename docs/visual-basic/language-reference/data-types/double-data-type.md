---
title: "Double — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Double
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad0e8082edfb7b7d96b0ca2019da88514e5b3b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="double-data-type-visual-basic"></a>Double — Typ danych (Visual Basic)
Blokad podpisany IEEE 64-bitowych (8-bajtowych) podwójnej precyzji liczb zmiennoprzecinkowych, które mają wartość z zakresu od - 1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych i z 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 do wartości dodatnie. Liczby o podwójnej precyzji przechowywać zbliżenia liczba rzeczywista.  
  
## <a name="remarks"></a>Uwagi  
 `Double` — Typ danych przewiduje liczbą wielkości największych i najmniejsze możliwe.  
  
 Wartość domyślna `Double` ma wartość 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Precyzja.** Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci. Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Końcowe zero.** Typy danych zmiennoprzecinkowych nie mają żadnych reprezentacji wewnętrznej końcowe zero znaków. Na przykład one rozróżnia 4.2000 i 4.2. W rezultacie końcowe zero znaki nie są wyświetlane po wyświetleniu lub drukowania wartości zmiennoprzecinkowych.  
  
-   **Znaki typu.** Znak literalny typu dołączanie `R` do literału wymusza `Double` — typ danych. Na przykład, jeśli wartość całkowitą następuje `R`, wartość jest zmieniana na `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Dołączanie znak typu identyfikator `#` dla wszystkich identyfikatorów wymusza `Double`. W poniższym przykładzie zmienna `num` jest typu `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Double?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Double?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal — typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Single — typ danych](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
