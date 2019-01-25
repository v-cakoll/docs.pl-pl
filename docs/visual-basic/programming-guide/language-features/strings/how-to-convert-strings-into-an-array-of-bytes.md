---
title: 'Instrukcje: Konwertowanie ciągów na tablice bajtów w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 83efc9e6b4d4433d5416f2f8b2612c76581586e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648485"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="28377-102">Instrukcje: Konwertowanie ciągów na tablice bajtów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28377-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="28377-103">W tym temacie pokazano, jak przekonwertować ciąg na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="28377-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28377-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="28377-104">Example</span></span>  
 <span data-ttu-id="28377-105">W tym przykładzie użyto <xref:System.Text.Encoding.GetBytes%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasy do przekonwertowania ciągu na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="28377-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 <span data-ttu-id="28377-106">Możesz wybrać spośród kilku opcji kodowania do przekonwertowania ciągu do tablicy typu byte:</span><span class="sxs-lookup"><span data-stu-id="28377-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="28377-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera Kodowanie zestawu znaków (7-bitowym) ASCII.</span><span class="sxs-lookup"><span data-stu-id="28377-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="28377-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów big-endian.</span><span class="sxs-lookup"><span data-stu-id="28377-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="28377-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.</span><span class="sxs-lookup"><span data-stu-id="28377-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="28377-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="28377-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="28377-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-32, używając kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="28377-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="28377-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.</span><span class="sxs-lookup"><span data-stu-id="28377-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="28377-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="28377-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28377-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28377-114">See also</span></span>
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [<span data-ttu-id="28377-115">Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28377-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
