---
title: "Single — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Single
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c91dbdf73ed1e26393518001ec8651557e5b780f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Decimal — typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double — typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
