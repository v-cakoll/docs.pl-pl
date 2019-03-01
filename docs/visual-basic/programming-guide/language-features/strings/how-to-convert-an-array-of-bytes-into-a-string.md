---
title: 'Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: cd091d743b04ef9d9709bde2b5a1205f3d7ae292
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979515"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Instrukcje: Konwertuj tablicę bajtów na ciąg w języku Visual Basic
W tym temacie pokazano, jak przekonwertować bajtów z tablicy bajtowej na ciąg.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Text.Encoding.GetString%2A> metody <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> kodowanie klasy w celu konwersji wszystkich bajtów z tablicy bajtów na ciąg.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Możesz wybrać kilka opcji kodowania do przekonwertowania na tablicę bajtów w ciąg:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera Kodowanie zestawu znaków (7-bitowym) ASCII.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów big-endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowania dla bieżącej strony kodowej ANSI systemu.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-16, używając kolejności bajtów little-endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowania dla formatu UTF-32, używając kolejności bajtów little-endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie w formacie UTF-8.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Instrukcje: Konwertowanie ciągów na tablice bajtów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
