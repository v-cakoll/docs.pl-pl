---
title: 'Instrukcje: Konwertowanie ciągów na tablice bajtów'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 3ee1d5e1e31054f23f4510c7a112d8e3473bcdd7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410609"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Porady: konwertowanie ciągów w tablice bajtów w Visual Basic
W tym temacie pokazano, jak przekonwertować ciąg na tablicę bajtów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano <xref:System.Text.Encoding.GetBytes%2A> metodę <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> klasy kodowania do przekonwertowania ciągu na tablicę bajtów.  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 Można wybrać jedną z kilku opcji kodowania, aby przekonwertować ciąg na tablicę bajtową:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera kodowanie dla zestawu znaków ASCII (7-bitowy).  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-16 przy użyciu kolejności bajtów big-endian.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowanie dla bieżącej strony kodowej ANSI systemu.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-16 przy użyciu kolejności bajtów little-endian.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-32 przy użyciu kolejności bajtów little-endian.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-8.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [Porady: konwertowanie tablicy bajtów w ciąg w Visual Basic](how-to-convert-an-array-of-bytes-into-a-string.md)
