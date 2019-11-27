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
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Porady: konwertowanie tablicy bajtów w ciąg w Visual Basic
W tym temacie pokazano, jak przekonwertować bajty z tablicy bajtowej na ciąg.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Text.Encoding.GetString%2A> klasy kodowania <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>, aby przekonwertować wszystkie bajty z tablicy bajtowej na ciąg.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Aby skonwertować tablicę bajtową na ciąg, można wybrać jedną z kilku opcji kodowania:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Pobiera kodowanie dla zestawu znaków ASCII (7-bitowy).  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-16 przy użyciu kolejności bajtów big-endian.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Pobiera kodowanie dla bieżącej strony kodowej ANSI systemu.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-16 przy użyciu kolejności bajtów little-endian.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-32 przy użyciu kolejności bajtów little-endian.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-7.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Pobiera kodowanie dla formatu UTF-8.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Instrukcje: konwertowanie ciągów na tablicę bajtów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
