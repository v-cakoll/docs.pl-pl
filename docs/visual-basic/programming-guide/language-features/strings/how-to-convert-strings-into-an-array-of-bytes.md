---
title: 'Porady: konwertowanie ciągów w tablice bajtów w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: da4a47b955b91f4bb39ecd7832da30d76e75d553
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="4c609-102">Porady: konwertowanie ciągów w tablice bajtów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c609-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="4c609-103">W tym temacie pokazano, jak przekonwertować ciąg na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="4c609-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c609-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c609-104">Example</span></span>  
 <span data-ttu-id="4c609-105">W tym przykładzie użyto <xref:System.Text.Encoding.GetBytes%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasę, aby przekonwertować ciąg na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="4c609-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 <span data-ttu-id="4c609-106">Możesz wybrać kilka opcji kodowania, aby przekonwertować ciąg na tablicę bajtów:</span><span class="sxs-lookup"><span data-stu-id="4c609-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="4c609-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera kodowanie znaków ASCII (7-bitowym) Ustaw.</span><span class="sxs-lookup"><span data-stu-id="4c609-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="4c609-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowanie formatu UTF-16, używając kolejności bajtów big endian.</span><span class="sxs-lookup"><span data-stu-id="4c609-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="4c609-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.</span><span class="sxs-lookup"><span data-stu-id="4c609-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="4c609-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowanie formatu UTF-16, używając kolejności bajtów little endian.</span><span class="sxs-lookup"><span data-stu-id="4c609-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="4c609-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowanie przy użyciu kolejności bajtów little endian formatu UTF-32.</span><span class="sxs-lookup"><span data-stu-id="4c609-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="4c609-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowania w formacie UTF-7.</span><span class="sxs-lookup"><span data-stu-id="4c609-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="4c609-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowania w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4c609-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c609-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c609-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [<span data-ttu-id="4c609-115">Porady: Konwertowanie tablicy bajtów w ciąg w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c609-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
