---
title: Double — Typ danych (Visual Basic)
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
ms.openlocfilehash: 701d10a334757a96ffd634204c1e1d5eb5418ce6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054448"
---
# <a name="double-data-type-visual-basic"></a>Double — Typ danych (Visual Basic)
Przechowuje podpisany IEEE 64-bitowych (8-bajtową) podwójnej precyzji liczb zmiennoprzecinkowych, z zakresu wartości od - 1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych i 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 do wartości dodatnich. Liczby o podwójnej precyzji przechowywać przybliżeniem liczbą rzeczywistą.  
  
## <a name="remarks"></a>Uwagi  
 `Double` Typu danych stanowi wielkości największą i najmniejszą możliwe podanie liczby.  
  
 Wartość domyślna `Double` wynosi 0.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Dokładność.** Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci. Może to spowodować nieoczekiwane wyniki z niektórych operacji, takich jak porównania wartości i `Mod` operatora. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Końcowe zera.** Typy danych zmiennopozycyjnych nie ma żadnych wewnętrznej reprezentacji końcowe zero znaków. Na przykład ich nie dokonuje rozróżnienia między 4.2000 i 4.2. W związku z tym zerowego znakami nie są wyświetlane po wyświetleniu lub drukowania wartości zmiennoprzecinkowych.  
  
- **Znaki typu.** Dołączanie znaku typu literał `R` do literału wymusza `Double` typu danych. Na przykład, jeśli jest poprzedzony wartością całkowitą z zakresu `R`, wartość zostanie zmieniona na `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Dołączanie znaku typu identyfikator `#` do jakiegokolwiek identyfikatora wymusza `Double`. W poniższym przykładzie zmienna `num` jest `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
- **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Double?displayProperty=nameWithType> struktury.  
  
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
