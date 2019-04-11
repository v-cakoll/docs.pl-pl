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
ms.openlocfilehash: ddb7b39f7a47234c003ca16e1d7ea013e113c108
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480888"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="f8bf3-102">Instrukcje: Konwertowanie ciągów szestnastkowych na numery (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8bf3-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="f8bf3-103">Ten przykład konwertuje ciąg szesnastkowy do liczby całkowitej przy użyciu <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="f8bf3-104">Aby przekonwertować ciągu szesnastkowego na liczbę</span><span class="sxs-lookup"><span data-stu-id="f8bf3-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="f8bf3-105">Użyj <xref:System.Convert.ToInt32(System.String,System.Int32)> metodę, aby przekonwertować numer wyrażone w base-16 na liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="f8bf3-106">Pierwszy argument <xref:System.Convert.ToInt32(System.String,System.Int32)> metody jest ciąg do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="f8bf3-107">Drugi argument opisuje jakie podstawowa, liczba jest będzie wyrażana; szesnastkowa to podstawa 16.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="f8bf3-108">Należy zwrócić uwagę na to, że ciąg szesnastkowy ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="f8bf3-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="f8bf3-109">Nie może zawierać `&h` prefiks.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="f8bf3-110">Nie może zawierać `_` separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="f8bf3-111">Jeśli prefiks lub separator cyfr jest obecna, wywołanie <xref:System.Convert.ToInt32(System.String,System.Int32)> metoda zgłasza wyjątek <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="f8bf3-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8bf3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8bf3-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
