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
ms.openlocfilehash: a96664f308a711d440f063627665283c5b7fc264
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967506"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Instrukcje: Konwertowanie ciągów na tablice bajtów w języku Visual Basic
W tym temacie pokazano, jak przekonwertować ciąg na tablicę bajtów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Text.Encoding.GetBytes%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasy do przekonwertowania ciągu na tablicę bajtów.  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 Możesz wybrać spośród kilku opcji kodowania do przekonwertowania ciągu do tablicy typu byte:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera Kodowanie zestawu znaków (7-bitowym) ASCII.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów big-endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów little-endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-32, używając kolejności bajtów little-endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie w formacie UTF-8.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
