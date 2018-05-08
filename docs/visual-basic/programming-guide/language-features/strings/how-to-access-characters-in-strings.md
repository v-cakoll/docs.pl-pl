---
title: 'Porady: dostęp do znaków w ciągach w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Porady: dostęp do znaków w ciągach w Visual Basic
W tym przykładzie przedstawiono sposób użycia <xref:System.String.Chars%2A> dostęp do znaków w określonej lokalizacji w ciągu dla właściwości.  
  
## <a name="example"></a>Przykład  
 Czasami jest przydatne do danych o znaki w ciągu i położenia tych znaków w ciągu. Można traktować jako tablicę znaków z ciągu (`Char` wystąpień); można pobrać określonego znaku odwołujące się do indeksu za pomocą znaku <xref:System.String.Chars%2A> właściwości.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index` Parametr <xref:System.String.Chars%2A> właściwość jest liczony od zera.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.String.Chars%2A> Właściwość zwraca znak na określonej pozycji. Jednak niektóre znaki Unicode może być reprezentowany przez więcej niż jednego znaku. Aby uzyskać więcej informacji na temat pracy z znaków Unicode, zobacz [porady: konwertowanie ciągu do tablicy znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Zgłasza właściwości <xref:System.IndexOutOfRangeException> wyjątek Jeśli `index` parametr jest większa lub równa długości ciągu, lub jeśli jest ona mniejsza od zera  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String.Chars%2A>  
 [Instrukcje: Konwertowanie ciągu na tablicę znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
