---
title: 'Instrukcje: konwertowanie tablicy bajtów na ciąg'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 8c1d9d1d2e89390873bc1c3dbb9623f047433a9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351975"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="dde52-102">Porady: konwertowanie tablicy bajtów w ciąg w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dde52-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="dde52-103">W tym temacie pokazano, jak przekonwertować bajty z tablicy bajtowej na ciąg.</span><span class="sxs-lookup"><span data-stu-id="dde52-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde52-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="dde52-104">Example</span></span>  
 <span data-ttu-id="dde52-105">W tym przykładzie zastosowano metodę <xref:System.Text.Encoding.GetString%2A> klasy kodowania <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>, aby przekonwertować wszystkie bajty z tablicy bajtowej na ciąg.</span><span class="sxs-lookup"><span data-stu-id="dde52-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="dde52-106">Aby skonwertować tablicę bajtową na ciąg, można wybrać jedną z kilku opcji kodowania:</span><span class="sxs-lookup"><span data-stu-id="dde52-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
- <span data-ttu-id="dde52-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera kodowanie dla zestawu znaków ASCII (7-bitowy).</span><span class="sxs-lookup"><span data-stu-id="dde52-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="dde52-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-16 przy użyciu kolejności bajtów big-endian.</span><span class="sxs-lookup"><span data-stu-id="dde52-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="dde52-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowanie dla bieżącej strony kodowej ANSI systemu.</span><span class="sxs-lookup"><span data-stu-id="dde52-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="dde52-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-16 przy użyciu kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="dde52-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="dde52-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-32 przy użyciu kolejności bajtów little-endian.</span><span class="sxs-lookup"><span data-stu-id="dde52-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="dde52-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.</span><span class="sxs-lookup"><span data-stu-id="dde52-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="dde52-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-8.</span><span class="sxs-lookup"><span data-stu-id="dde52-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde52-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dde52-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="dde52-115">Instrukcje: konwertowanie ciągów na tablicę bajtów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dde52-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
