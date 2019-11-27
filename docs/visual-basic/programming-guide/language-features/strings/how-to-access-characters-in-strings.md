---
title: 'Porady: dostęp do znaków w ciągach'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352461"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Porady: dostęp do znaków w ciągach w Visual Basic
W tym przykładzie pokazano, jak użyć właściwości <xref:System.String.Chars%2A>, aby uzyskać dostęp do znaku w określonej lokalizacji w ciągu.  
  
## <a name="example"></a>Przykład  
 Czasami warto mieć dane dotyczące znaków w ciągu i położenia tych znaków w ciągu. Ciąg można traktować jako tablicę znaków (`Char` wystąpienia). można pobrać konkretny znak, odwołując się do indeksu tego znaku za pomocą właściwości <xref:System.String.Chars%2A>.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index` parametr właściwości <xref:System.String.Chars%2A> jest oparty na zero.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Właściwość <xref:System.String.Chars%2A> zwraca znak w określonej pozycji. Jednak niektóre znaki Unicode mogą być reprezentowane przez więcej niż jeden znak. Aby uzyskać więcej informacji na temat sposobu pracy z znakami Unicode, zobacz [How to: Convert a String to array of characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 Właściwość <xref:System.String.Chars%2A> zgłasza wyjątek <xref:System.IndexOutOfRangeException>, jeśli parametr `index` jest większy lub równy długości ciągu lub jeśli wartość jest mniejsza od zera  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.String.Chars%2A>
- [Instrukcje: Konwertowanie ciągu na tablicę znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Konwertowanie między ciągami a innymi typami danych w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
