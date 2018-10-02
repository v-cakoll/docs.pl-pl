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
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863107"
---
# <a name="single-data-type-visual-basic"></a>Single — Typ danych (Visual Basic)
Przechowuje podpisany IEEE 32-bitowe (4-bajtową) pojedynczej precyzji liczb zmiennoprzecinkowych z zakresu od - 3.4028235E + 38 do - 1, 401298E-45 dla wartości ujemnych i 1, 401298E-45 za pośrednictwem 3.4028235E + 38 dla wartości dodatnich. Liczby o pojedynczej precyzji przechowywać przybliżeniem liczbą rzeczywistą.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Single` typu danych, które zawierają wartości zmiennoprzecinkowych, które nie wymagają szerokość pełnych danych `Double`. W niektórych przypadkach środowiska uruchomieniowego języka wspólnego może być możliwe umieszczenie usługi `Single` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.  
  
 Wartość domyślna `Single` wynosi 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Dokładność.** Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać o tym, że nie zawsze mają dokładne reprezentacji w pamięci. Może to spowodować nieoczekiwane wyniki z niektórych operacji, takich jak porównania wartości i `Mod` operatora. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Rozszerzanie.** `Single` — Typ danych rozszerza się na `Double`. Oznacza to, że możesz przekonwertować `Single` do `Double` nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
-   **Końcowe zera.** Typy danych zmiennopozycyjnych nie ma żadnych wewnętrznej reprezentacji końcowych 0 znaków. Na przykład ich nie dokonuje rozróżnienia między 4.2000 i 4.2. W związku z tym końcowych 0 znaków nie są wyświetlane, gdy możesz wyświetlić lub wydrukować różne wartości zmiennoprzecinkowe.  
  
-   **Znaki typu.** Dołączanie znaku typu literał `F` do literału wymusza `Single` typu danych. Dołączanie znaku typu identyfikator `!` do jakiegokolwiek identyfikatora wymusza `Single`.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Single?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Single?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Decimal, typ danych](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double, typ danych](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
