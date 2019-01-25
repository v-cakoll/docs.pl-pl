---
title: 'Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 577cce6322bf80bf2abdb963f07938b1a8b5d174
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718354"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="56ba6-102">Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56ba6-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="56ba6-103">W tym temacie pokazano, jak przekonwertować bajtów z tablicy bajtowej na ciąg.</span><span class="sxs-lookup"><span data-stu-id="56ba6-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ba6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="56ba6-104">Example</span></span>  
 <span data-ttu-id="56ba6-105">W tym przykładzie użyto <xref:System.Text.Encoding.GetString%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasy w celu konwersji wszystkich bajtów z tablicy bajtów na ciąg.</span><span class="sxs-lookup"><span data-stu-id="56ba6-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 <span data-ttu-id="56ba6-106">Możesz wybrać kilka opcji kodowania do przekonwertowania na tablicę bajtów w ciąg:</span><span class="sxs-lookup"><span data-stu-id="56ba6-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="56ba6-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera Kodowanie zestawu znaków (7-bitowym) ASCII.</span><span class="sxs-lookup"><span data-stu-id="56ba6-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="56ba6-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów big-endian.</span><span class="sxs-lookup"><span data-stu-id="56ba6-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="56ba6-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.</span><span class="sxs-lookup"><span data-stu-id="56ba6-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="56ba6-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="56ba6-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="56ba6-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-32, używając kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="56ba6-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="56ba6-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.</span><span class="sxs-lookup"><span data-stu-id="56ba6-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="56ba6-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="56ba6-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ba6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56ba6-114">See also</span></span>
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="56ba6-115">Instrukcje: Konwertowanie ciągów na tablice bajtów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56ba6-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
