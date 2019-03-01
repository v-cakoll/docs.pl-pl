---
title: 'Instrukcje: Dostęp do znaków w ciągach w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: f2831333008844c959c3625698fce6c485450683
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967558"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Instrukcje: Dostęp do znaków w ciągach w Visual Basic
W tym przykładzie przedstawiono sposób użycia <xref:System.String.Chars%2A> właściwość dostęp do znaków w określonej lokalizacji w ciągu.  
  
## <a name="example"></a>Przykład  
 Czasami przydatne jest zapewnienie dane dotyczące znaków w ciągu i położenie tych znaków w ciągu. Można traktować jako tablicę znaków ciągu (`Char` wystąpień); można pobrać określonego znaku, odwołując się do indeksu za pomocą znaku <xref:System.String.Chars%2A> właściwości.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index` Parametru <xref:System.String.Chars%2A> właściwość jest liczony od zera.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.String.Chars%2A> Właściwość zwraca znak w określonej pozycji. Jednak niektóre znaki Unicode mogą być reprezentowane za więcej niż jeden znak. Aby uzyskać więcej informacji na temat sposobu pracy ze znakami Unicode, zobacz [jak: Konwertowanie ciągu na tablicę znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Zgłasza właściwości <xref:System.IndexOutOfRangeException> wyjątek Jeśli `index` parametru jest większa lub równa długości ciągu, czy go jest mniejsza niż zero  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.String.Chars%2A>
- [Instrukcje: Konwertowanie ciągu na tablicę znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
