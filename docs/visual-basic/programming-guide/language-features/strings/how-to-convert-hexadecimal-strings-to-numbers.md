---
title: 'Instrukcje: Konwertowanie ciągów szestnastkowych na numery (Visual Basic)'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: c8ef615b6874642fa9ad1b22fe9d7f7745d4ffde
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201004"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="1100a-102">Instrukcje: Konwertowanie ciągów szestnastkowych na numery (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1100a-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="1100a-103">Ten przykład konwertuje ciąg szesnastkowy do liczby całkowitej przy użyciu <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1100a-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="1100a-104">Aby przekonwertować ciągu szesnastkowego na liczbę</span><span class="sxs-lookup"><span data-stu-id="1100a-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="1100a-105">Użyj <xref:System.Convert.ToInt32(System.String,System.Int32)> metodę, aby przekonwertować numer wyrażone w base-16 na liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="1100a-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="1100a-106">Pierwszy argument <xref:System.Convert.ToInt32(System.String,System.Int32)> metody jest ciąg do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="1100a-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="1100a-107">Drugi argument opisuje jakie podstawowa, liczba jest będzie wyrażana; szesnastkowa to podstawa 16.</span><span class="sxs-lookup"><span data-stu-id="1100a-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]  

- <span data-ttu-id="1100a-108">Należy zwrócić uwagę na to, że ciąg szesnastkowy ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1100a-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="1100a-109">Nie może zawierać `&h` prefiks.</span><span class="sxs-lookup"><span data-stu-id="1100a-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="1100a-110">Nie może zawierać `_` separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="1100a-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="1100a-111">Jeśli prefiks lub separator cyfr jest obecna, wywołanie <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda zgłasza wyjątek <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="1100a-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1100a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1100a-112">See also</span></span>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
