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
ms.openlocfilehash: 786065fde9814d31ac36b56e1455d5b1685122ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665354"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="28a0c-102">Instrukcje: Konwertowanie ciągów na tablice bajtów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28a0c-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="28a0c-103">W tym temacie pokazano, jak przekonwertować ciąg na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="28a0c-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28a0c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="28a0c-104">Example</span></span>  
 <span data-ttu-id="28a0c-105">W tym przykładzie użyto <xref:System.Text.Encoding.GetBytes%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasy do przekonwertowania ciągu na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="28a0c-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 <span data-ttu-id="28a0c-106">Możesz wybrać spośród kilku opcji kodowania do przekonwertowania ciągu do tablicy typu byte:</span><span class="sxs-lookup"><span data-stu-id="28a0c-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
- <span data-ttu-id="28a0c-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera Kodowanie zestawu znaków (7-bitowym) ASCII.</span><span class="sxs-lookup"><span data-stu-id="28a0c-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="28a0c-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów big-endian.</span><span class="sxs-lookup"><span data-stu-id="28a0c-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="28a0c-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.</span><span class="sxs-lookup"><span data-stu-id="28a0c-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="28a0c-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="28a0c-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="28a0c-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-32, używając kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="28a0c-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="28a0c-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.</span><span class="sxs-lookup"><span data-stu-id="28a0c-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="28a0c-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="28a0c-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a0c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28a0c-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [<span data-ttu-id="28a0c-115">Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28a0c-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
