---
title: 'Porady: dostęp do znaków w ciągach'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: fa5920cfd25f61f6e6c7d5438ef7c0e38a48fa1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401956"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Porady: dostęp do znaków w ciągach w Visual Basic
W tym przykładzie pokazano, jak użyć <xref:System.String.Chars%2A> właściwości w celu uzyskania dostępu do znaku w określonej lokalizacji w ciągu.  
  
## <a name="example"></a>Przykład  
 Czasami warto mieć dane dotyczące znaków w ciągu i położenia tych znaków w ciągu. Można traktować ciąg jako tablicę znaków ( `Char` Instances); można pobrać konkretny znak, odwołując się do indeksu tego znaku za pomocą <xref:System.String.Chars%2A> właściwości.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`Parametr <xref:System.String.Chars%2A> właściwości jest oparty na zero.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.String.Chars%2A>Właściwość zwraca znak na określonej pozycji. Jednak niektóre znaki Unicode mogą być reprezentowane przez więcej niż jeden znak. Aby uzyskać więcej informacji na temat sposobu pracy z znakami Unicode, zobacz [How to: Convert a String to array of characters](how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A>Właściwość zgłasza <xref:System.IndexOutOfRangeException> wyjątek `index` , jeśli parametr jest większy niż lub równy długości ciągu lub jeśli wartość jest mniejsza od zera  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.String.Chars%2A>
- [Porady: konwertowanie ciągu do tablicy znaków](how-to-convert-a-string-to-an-array-of-characters.md)
- [Konwertowanie pomiędzy ciągami a innymi typami danych w Visual Basic](converting-between-strings-and-other-data-types.md)
- [Ciągi](index.md)
