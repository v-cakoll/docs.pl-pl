---
title: "Porady: konwertowanie ciągów szestnastkowych na numery (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: petrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: c35ac615e3f87710f934a1cf66e6546625298bd0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Porady: konwertowanie ciągów szestnastkowych na numery (Visual Basic)
W tym przykładzie konwertuje ciąg szesnastkowy całkowitą przy użyciu <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Aby przekonwertować ciąg szesnastkowy na liczbę  
  
-   Użyj <xref:System.Convert.ToInt32(System.String,System.Int32)> metodę, aby przekonwertować liczby wyrażone w base-16, do liczby całkowitej.  
  
     Pierwszy argument funkcji <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda jest ciąg do przekonwertowania. Drugi argument opisuje jakie base numer jest wyrażona w; szesnastkowe jest podstawowy 16.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- Należy pamiętać, że ciąg szesnastkowy ma następujące ograniczenia:

   - Nie może zawierać `&h` prefiks.
   - Nie może zawierać `_` separator cyfr.

   Jeśli prefiks lub separator cyfr jest obecna, wywołanie <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda zgłasza <xref:System.FormatException>.

## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
